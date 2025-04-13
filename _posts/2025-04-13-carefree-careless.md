---
layout: post
title: Vibe Coding without worry or care
---

### Without a worry
At this point in time, [Vibe Coding](https://x.com/karpathy/status/1886192184808149383?lang=en) is probably even past the hype cycle. Just describing to cursor what you want to do and having the editor generally get it right has been extremely liberating for me and many people. My drive to build things in software had waned, mainly because setting up new projects tended to be a lot of busywork. But with Cursor those pieces of busywork are now hyper automated. I don't have to **worry** about being derailed due to e.g. updated interfaces to libraries, I can just tell Cursor to "fix it" and continue my main quest. 

I feel **carefree** building things with my trustee Agent flow

As someone who mainly used tmux/vim/neovim for the last 12 years, I feel like I can't switch back (maybe avante.nvim will get better with smart completions, but I just don't think it ever will get there sadly). Cursor has given me back some of the joy of building things again. 

At least building brand _new_ things...

### Without care

But over the last couple of months of building things with Cursor, I'm noticing that I'm much more confused about things. There are comments in the code i'm looking at that don't make sense given the actual code. Reviewing pull requests is much more difficult because I know the codebase less well than I'm use to. There are fewer and fewer abstractions, and more and more utility functions. Complexity is never reduced when using Cursor agent, just added. 

Take Tailwind as an example. Cursor is amazing at figuring out how to fix UI/layout issues when you tell it what you're seeing and tell it what you want. But it also has a tendency to add extraneous tailwind classes that don't actually _do_ anything either. And when it comes to reviewing a PR, it's basically impossible to tell what the _intention_ behind the hierarchy of tailwind layout classes.

With much more code and functions being generated and duplicated, I am absorbing the structure and content of the code much less than I am used to as well, and relying on the model to be able to explain things to me. I have less intuition about the right way to do things.

I'm much more likely to be **careless** when relying on Cursor to build things on my behalf.