---
layout: post
title: "What Six Months of Code Review Taught Me About Writing Software"
date: 2025-06-01
categories: [Engineering]
read_time: 6
description: "The difference between code that works and code that communicates — and why that gap matters more than I expected."
---

There's a version of software engineering where you write code that does what it's supposed to do, push it, and move on. 

Then there's the version where you work with other engineers who read your code, question your decisions, and push back on your naming choices. That version is significantly harder. It's also the one that makes you a better engineer faster than anything else.

Six months into a professional engineering environment at Semicolon Africa, I can say the most valuable thing I've experienced isn't a framework, a tool, or a language feature. It's code review. Not just having my code reviewed, but reviewing其他人的代码 as well. Both sides taught me things I didn't expect.

## What code review actually is

Most people think code review is about catching bugs. Sometimes it is. But the deeper purpose is knowledge transfer — a structured way for a team to share mental models, maintain consistency, and surface assumptions before they calcify into production problems.

When a senior engineer looks at your PR and asks "what's the intent behind this function name?" they're not being pedantic. They're telling you that the code doesn't communicate clearly enough to be maintained by someone who wasn't in your head when you wrote it. This is the fundamental shift: code is not instruction for machines — it's communication with humans.

The best reviews I've received weren't the ones that caught the most bugs. They were the ones that challenged my approach. A comment like "this works, but have you considered an alternative pattern?" is worth more than ten typo fixes because it changes how you think about future problems.

## The naming problem

I had a function called `handleData`. It handled some data. What data? What kind of handling? I couldn't answer those questions quickly — which meant the function name had failed its only job.

The review comment was short: *"What does this do?"*

I rewrote it as `normalizeIncomingFeedbackPayload`. Verbose? Yes. But now any engineer on the team knows what it does without reading the implementation. That's the trade-off, and it's usually worth it.

This pattern repeated across dozens of PRs. A boolean flag called `flag` that controlled whether emails were sent became `shouldSendEmailNotification`. A variable called `temp` that held a parsed date became `parsedExpiryDate`. Each rename felt small in isolation, but collectively they transformed the codebase from something you had to decipher into something you could read.

Six months in, I've learned that good naming is the most cost-effective documentation you can write. It never goes out of sync with the code because it *is* the code.

## Tests as documentation

Before code reviews, I wrote tests to satisfy a coverage threshold. After a few months of review, I understand tests differently — they document the expected behavior of a system for the next person who touches it.

A test called `it('should work')` tells the reader nothing. A test called `it('returns 400 when email field is missing from request body')` is a specification. Future-you, reading that test six months from now, will thank current-you.

I started writing test names that read like sentences describing specific scenarios. Each test became a mini-specification. When a new engineer joined the team, they could understand the system's contract by reading the test descriptions without diving into implementation details.

This changed how I wrote code too. When I couldn't easily write a test for a function, it was usually because the function did too many things. Hard-to-test code is often poorly designed code. The test became a forcing function for better architecture.

## Reading code is a skill

Before my first code review rotation, I thought reading code was something you just did as needed. I didn't realize it was a skill you had to develop, like writing code or debugging.

I learned to read PRs systematically: start with the tests to understand intent, then read the implementation, then check edge cases. I learned to ask questions about why something was done a certain way, not just whether it worked. And I learned that the most valuable review comments are often about what's missing — the error case not handled, the validation not added, the comment not written.

Reviewing other people's code made me a better writer too. Seeing someone else's elegant solution to a problem I had struggled with taught me patterns I could apply in my own work. Seeing common mistakes helped me recognize them in my own code before I submitted it.

## The emotional side

No one talks about how code review feels when you're starting out. The first time someone left ten comments on your PR, your stomach drops. It feels personal, even when it isn't.

I learned to separate my ego from my code. A comment on my code wasn't a judgment of me as an engineer. It was an opportunity to make the code better. The engineers whose opinions I valued most were the ones who left the most comments — because they cared enough to read carefully.

I also learned how to receive feedback gracefully. Thank the reviewer. Ask clarifying questions. Don't defend code that isn't clear — if someone misunderstood it, the code needs to change, not the reader.

## Writing reviewable PRs

The biggest lesson: you can make your reviewer's job easier by writing reviewable PRs from the start. Small, focused commits with descriptive messages. PRs that do one thing and do it well. Self-review before submission — catch the typos, the leftover console.logs, the missing error handlers before anyone else has to.

A good PR tells a story. The description explains what it does and why. The commits break the work into logical steps. The diff is as small as possible. When your reviewer can understand your PR in five minutes instead of thirty, everyone wins.

## The real lesson

Code review teaches you to write software for two audiences simultaneously: the computer that runs it, and the human who reads it. Most early-career engineers only think about the first one.

The moment you start thinking about the second, your code quality changes permanently. You write self-documenting code. You structure your PRs for readability. You treat tests as specifications. And you stop seeing review comments as criticism and start seeing them as free education.

Six months in, I've learned that the best engineers aren't the ones who write the most code. They're the ones whose code is easiest for others to understand and build upon. Code review taught me that.

---

*Working through my own engineering journey at Semicolon Africa. More notes like this at [meethybrid.github.io/blog]({{ '/blog' | relative_url }}).*
