---
layout: post
title: Code for Debugging pt 1 - pt 1
---

There are tons of posts on the internet about how to write code. There are blogs emphasizing readability when writing code. There are plenty of essays, even books about how to write code that is easy to extend and add functionality. While I think emphasizing readability and adding functionality are important qualities of writing scalable code, I think there's not as much stuff out there about how to write code that's easy to debug. I'm hoping to write more of these, but here's one lesson I've learned on making code easier to untangle and debug.

## Remove Generic Parameters if you can
Imagine you get a bug report that says the following:
```
Customer seeing "Error: Bad Request Param" when updating billing info
```
What steps are you going to take in order to debug this report? Here's some ideas -
1) See if we have a request ID to see if there's any other info in the logs
2) See if our bugsnag/sentry/bug catching software caught this error
3) maybe try to grep for that string in the code base?

I think all of these approaches are pretty valid. Let's say, after tracing steps 2 or 3, you find the error is probably getting thrown from the following set of lines

```
def update_customer_billing(params)
  service.update_billing(customer_id, params)
rescue BillingError => e
  raise Error(e.message)
end
```

Actually first - I don't accept the premise that I'd have found it by following steps 2 or 3. Bugsnag may have swallowed the originating cause of the error or hid it among a bunch of other errors. and what exactly do I grep for? "billing"?

(This is example is a bit simplistic, but I'm less concerned about the bad masking of the exception is, and more concerned with the line invoking the service.)

Anyway, let's just say I found the general place where the error occured. Reading this code - I have no clue what are valid parameters to update the customer's billing info. Actually I don't even know if `customer_id` was valid or not. The error says "Bad Request Param", But what are the params that are bad?

What if the code read as follows?

```
def update_customer_billing(params)
  service.update_billing(customer_id, plan: params.plan)
rescue BillingError => e
  raise Error(e.message)
end
```

Now we're specifying `plan` as the params - this gives us way more context. It's way easier to understand what the params are. Yeah sure, it's less generic; if we want to allow more params to be passed (i.e. if we want to allow customers to alter other aspects of their billing info via some params), we have to add more params to this keyword list. 

Here, I think the general pattern to avoid is overgeneralization. Generic parameters - passing whole hash/dicts/whatever your language uses  - can make it easier in the future to dynamically add arguments to function calls, but you have to be much more deliberate about what value that adds to the system. I think it's critical to evaluate whether all the parameters are actually generic - do they all have equal weight, do we expect clients to speicify relatively unknown values?

A trickier example of this is search parameters. Let's say you're building out an endpoint to search across multiple facets of a resource. And let's say, for v1, you need to search across 5 different facets of the model - name, date created, creator, state, and a note field. The client will have to pass a fairly detailed set of parameters on how the user wants to filter results across all these parameters. But when searching fails due to an unforseen issue, it's much harder to debug

```
def search(where_clauses)
  Model.where(where_clauses)
end
```

than it is to debug

```
def search(name_filter, created_at_filter, creator_filter, state_filter, note_filter)
  Model.where(
    name: name_filter,
    created_at: created_at_filter,
    creator_filter: creator_filter,
    state_filter: state_filter,
    note_filter: note_filter
  )
end
```

Now, let's say that we have an additional three or four filters that we want to search against. Does this pattern scale? I mean, to be honest it really really depends on your use case. It may not scale if the number of facets we're searching against changes rapidly and are very dynamic by nature. However, if things are static, or not often changing, there's greater value in specifying the parts in code than there is in specifying them in some kind of hash/dict/array/generic data structure. You get cleaner stack traces, it's easier to understand what variables contain, at the expense of being more verbose.

A part of this is about coding for readability, but I think there's something deeper than just coding for readability; If I was joining a new team with a codebase I was unfamiliar with, and I receved a bug report, I want to be able to tie what the user is experiencing with what the code actually looks like. There are more opportunities to optimize for debuggability which I hope to cover in future posts
