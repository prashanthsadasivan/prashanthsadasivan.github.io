---
layout: post
title: Understanding is not binary because problems are multi-dimensional
---
In the past, I've been guilty of assuming that I understand someone's problem. "Got it, what about if you...." I've said, cutting the other person off mid-sentence while silently congratulating myself for saving the other person from the burden of speaking their mind. I cringe when I think about times when I've done this, and I try not to do this any more.

Now, when I'm trying to make sure I understand a problem or an ask from someone, I never feel like I understand it completely. I've come to see there's no such thing as "getting it", or perfect empathy. Understanding is not "Yes I get it" or "No I don't get it" (this is pretty obvious). And there are many different ways to understand what "it" is (less obvious, but somewhat so). Understanding is continuous, not binary because problem spaces are multi-dimensional. Thinking about the dimensions of a problem-space and degrees of understanding is a good way to pause and reflect my own certainty. It's also a useful way for me to structure my understanding of someone's perspective, and informs how I might advocate for my own position more effectively.

## The infamous HN Dropbox comment

When Dropbox [launched on HN](https://news.ycombinator.com/item?id=8863), the top comment is well known as an iconic HN forum response. The comment has a bit worse reputation for 'not getting it' than the original text of the comment, but I think it shows the perils of having a binary understanding of a multi-dimensional problem. The comment's main issues with Dropbox are

1. This is already solvable using FTP + Version Control
2. The solution is also distributed to end users by default
3. Network file syncing doesn't work for a lot of cases which is why you can't replace a USB drive.

This is a great example of understanding the problem _along a specific dimension_. It's actually a _very_ insightful comment - existing solutions that are _already distributed_ to end users is a very difficult dynamic to overcome (just ask Slack about the power of distribution as a competitor to M$FT Teams). There are kernels of serious questions embedded in this comment, and the person raising these questions is at least somewhat well informed about solutions in the space of file syncing. The point about USB drives is also very sharp - at the time, cellular data was definitely not widely accessible, and WiFi was (more of) a crapshoot. If I were thinking about whether the commenter has a working understanding of the problem space in file syncing, I'd lean towards "Yeah" if forced to pick between Y/N.

## Problem spaces are multi-dimensional, and understanding happens along each dimension

Obviously, however, understanding is not a yes or no (which should be obvious given how things ended up for [DBX](https://www.google.com/finance/quote/DBX:NASDAQ)). Specifically in this case, I'd say the commenter _sorta_ understood the dynamics of file syncing solutions, but not completely. Here are some ways aspects of file syncing I'd say the first comment didn't fully understand.

1. Even combining the tools mentioned doesn't really replicate the same dynamics that Dropbox introduced. While you could access the files via an FTP server, they wouldn't automatically be synced between the devices (unless they all ran the Linux / syncing solution they mentioned)
2. As drew [mentions](https://news.ycombinator.com/item?id=9272), the issues with file sync on the windows weren't really solved
3. The "Throw away your USB drive" language was specifically around syncing files during periods of intermittent connectivity across your own machines, not between shared devices.

I'm not pointing these shortcomings out just to dunk on the original commenter, but to show that even someone who is well informed on file syncing may not have full understanding of it. (If it's not clear by now, I actually thought their feedback was very well communicated.)

Zooming out even more, file syncing itself is a solution to human problems - the problem space is not file syncing software. Why do people even need to transfer files between computers? There are tons of reasons - collaboration, backups, file versioning, users with multiple devices, and others. And what about the current state of how people use and interact with files at all? The state of the art technology at the time? Each one of these are a dimension to the problem space, and every solution be evaluated along these various dimensions differently. The original comment's solution fits well along some of these dimensions, but doesn't fit well along others. Problems spaces are multi- dimensional, and one's understanding of a problem space can be evaluated along all of the various dimensions in the space. 

Examining Dropbox a bit closer, the dimensions of the problem space they really understood were:
1. Where do the majority of users live? Focusing on Windows and Mac versus technical users.
2. How do they use/interact with files? - Users used Windows Explorer or Mac Finder to interact with files. They made software that let them use the tools they already know how to use (no need to understand FTP). People also never thought about having "multiple copies" of a file - they thought of "the document", and wanted it to be available no matter where they worked.
3. Collaboration on files sucked - emailing files, versioning files, collaborating on edits was just impossible.
4. Passive backups sucked - they either required manual checkpoints, or involved a ton of bandwidth to sync whole files instead of optimizing for continuous syncing
5. USB drives just sucked too. They got lost, had outdated copies of files, ran out of storage so you'd end up with multiple of them (exacerbating the issues)

Their understanding of the problem space was much deeper along many of it's facets. And it's important to point out also that not every dimension in the space is equally weighted. They built a product based on understanding the important dimensions of the problem space that lived _where their target users lived_ and around what they were _trying_ to do. They also benefited from various trends in technology which I think also shows a deeper understanding of the dynamics in technology and industry. Wireless networks were becoming much more reliable, and the growth in cloud software / software that worked seamlessly via the internet changed users expectations to align with how Dropbox worked. One could even argue Dropbox was one of the driving forces of those changing user expectations.

## Structured empathy, and the follow up to the infamous HN comment

I don't know how insightful of an observation this is, but I have found it useful when trying to probe my own certainty. In situations where I feel very certain about The Right Answer™️, but others seem to be doubtful or uncertain, I try to identify the dimensions of the problem that I have more understanding of, and also look for dimensions I am not accounting for. Maybe I do understand the different facets, but maybe I'm weighing one dimension much more importantly than it should be weighed. 

Conversely, in trying to explain and advocate my own opinion to others, I can listen to someone, evaluate their perspective the in a similar fashion. By listening and asking questions, I can see what dimensions of the problem they aren't considering, what dimensions they are weighing more than I am, and explain the differences in a more structured way.

I'd feel remiss if I didn't highlight the followup [comment](https://news.ycombinator.com/item?id=9479) replying to Drew. The reputation this thread has for demonstrating classic HN cynicism is overblown in my view. In response to some of the points Drew raised, the commenter was really positive, energizing, and acknowledged the shortcomings of their original comment. While there is clearly some skepticism even still, I think the thread is actually an exemplar of expressing one's understanding of a problem, debating and exploring the problem space, and learning from different perspectives. Maybe I'm reading too much into it, or maybe there's some context I'm missing, but I find the whole thread very wholesome.

### Random thoughts, responses to comments, and edits

#### Thoughts
* Originally I had planned to make some sort of AI reference around neural networks, tensors, weights and biases, but it just felt too forced.
* It was hard to come up with an example that wasn't too contrived, too specific, or too long-winded. The Dropbox comment thread is well known, so I thought it was best to choose a public example that wouldn't require a lot of explanation, versus a personal or hypothetical example that might require a lot of context to convey the point.

