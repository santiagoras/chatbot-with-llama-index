# Introduction

This document aims to record the practices we (try to) follow for development in the project.

Just like a `runbook.md` explains how to run things, a `contributing.md` provides guidelines to contribute to the project, this `practices.md` focus on practices surrounding the development of the project. The document serves both as an onboarding material for newcomers, and as a point of reference for discussions.

These guidelines are not hard rules and they are not set in stone. They are a compendium of knowledge that we have attained from different projects, so we have a good degree of confidence in them. Feel free to open up an RFC with proposed changes if the team’s practices have changed :)

## About code

**AC1** Code is written once but read and re-written many times. Focus on readability, unless you’re refactoring code to make it more performant.

**AC2** Write modular and reusable code. There are two parts to it:
Break the code into smaller pieces each intended to perform a specific task (may include sub-tasks)
Group these functions into modules (or python files) based on their usability. It also helps with staying organized and enhances code maintainability.
Two key principles to follow are [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) and [SOLID](https://adevait.com/software/solid-design-principles-the-guide-to-becoming-better-developers).

**AC3** Don’t fuss about formatting. Let linters and formatters take care of things. Please don’t silence warnings unless strictly necessary. And if you do, try to silence them in the line or file that is causing issues instead of silencing them globally in the configuration file.

**AC4** All functions that are part of the API or have public usage from other modules should have complete docstrings. Look at [numpy’s docstring documentation](https://numpydoc.readthedocs.io/en/latest/format.html) as an example. Internal and private functions can get away with simple descriptions.

**AC5** When possible, add unit tests to the code. Break down functions into smaller parts if needed.

## About communication

**AX1** Prefer written over oral. For quick iterations, short syncs make sense. Strive to write and share summaries of oral meetings so that they serve future you and others.

**AX2** Prefer public over private channels for discussions – see [Metcalfe’s law](https://en.wikipedia.org/wiki/Metcalfe%27s_law). Even if you are sure a specific person can answer your question, the answer might be useful to everybody.

**AX3** It’s perfectly normal to find delays and roadblocks when completing tasks. When these happen, try to communicate them as early as possible so everyone is on the same page. Maybe someone can help, and common delays or roadblocks can be mitigated.

**AX4** When you need help debugging something, please share enough information to reproduce the problem, so that another person can troubleshoot it locally. StackOverflow has a [good guide on Minimal Reproducible Examples](https://stackoverflow.com/help/minimal-reproducible-example). In our case, pushing code to a branch and providing a step-by-step guide to reproduce the problem is often enough.

**AX5** If you stumbled upon a weird bug or scenario and solved it, share your solution! We are always interested in learning and your solution might help others.

## About project contributions

**AP1** Focus on having a quick work-in-progress (WIP) merge request that is end-to-end, and then iterate.

**AP2** Before setting your merge request to RFC, be your own reviewer! Make sure the code works, that it follows good practices and that everything is documented. Read more on Michael Lynch’s [_How to make your code reviewer fall in love with you_](https://mtlynch.io/code-review-love/).

**AP3** Write a good RFC description: what the changes are, why they were necessary, why the changes were implemented in that way. Also, detail a bit how to review the RFC and how to check that it works!

**AP4** When someone is waiting for a code review, they are blocked by others. Try to start the code review as soon as you can.

**AP5** On the other side - be mindful of your reviewer’s time, since reviewing code is a context switch and therefore takes a mental toll. Try to always request a review from code that you think is ready to be sent to prod.

**AP6** On the topic of reviewing someone else’s code, Lynch also has a series on Human Code Reviews ([I](https://mtlynch.io/human-code-reviews-1/), [II](https://mtlynch.io/human-code-reviews-2/)). Here are some key points:

* **AP6.1** Start on high level comments and work your way down.
* **AP6.2** Try to remove the subject from the sentence, and frame feedback as requests instead of commands. The code is not owned by any single person, it is the team’s, so we should focus on that viewpoint. Likewise, it’s usually more tactful to request something instead of demanding it.
* **AP6.3** Tie notes to principles, not opinions. Explain why something should be changed in the context of best practices instead of demanding it out of opinion or preference.
* **AP6.4** Offer sincere praise. Code reviews are usually concerned with improving the solution, but it’s also a great moment to highlight parts that you liked or things that you learned.
* **AP6.5** Grant approval when the remaining changes are trivial or optional suggestions.

Google also has nice guides on [how to write code review comments](https://google.github.io/eng-practices/review/reviewer/comments.html) and on [how to handle conflicts in code reviews](https://google.github.io/eng-practices/review/reviewer/pushback.html).

**AP7** RFCs that include change in functionality should update relevant documentation whenever possible (the readme.md, contributing.md, etc.), and reviewers should enforce this. It’s better to keep it up to date incrementally than to wait for it to go stale.

## About deployments to production

**AD1** Setting up a weekly deployment day can help set a work rate. Avoid Fridays for most deployments when possible!

**AD2** Merging to the production branches should always require at least one approval. Even for small changes, having another set of eyes can make a big difference.

**AD3** Sometimes things go wrong. It’s okay, and no-one should bear the full responsibility for it; the team wins and loses together. In these scenarios: be up front, communicate and act optimistically. When the issue is solved, be sure to write up a post-mortem about it  (see [here for examples](https://github.com/dastergon/postmortem-templates)) and try to deduce actionables that will minimize problems in the future.

**AD4** Create and maintain an up-to-date runbook with all the details of how to run the project and deploy it to production, along with common issues and frequently asked questions.