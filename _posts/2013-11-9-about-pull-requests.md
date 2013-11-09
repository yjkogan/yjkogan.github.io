#Pull Requests: Witty Sub-Title

Pull requests are a fantastic tool for collaborating on a coding project. A great starting point is a video called ["How Github uses Github to build Github"](http://www.youtube.com/watch?v=qyz3jkOBbQY), which my friend [Sidd](https://twitter.com/sidd) showed me a while back. My aim in this post is to describe the experiences that have led me to love pull requests in the hope of inspiring more people to use them. At a high level, pull requests are great for:

* Encouraging code reviews and discussions of code structure
* Keeping your team up to date on what you're doing and why
* Maintaining a bug-free repository with a clean and descriptive commit history

### A Case Study
When I first joined Romotive, we weren't using pull requests at all. We did our best to talk with each other before merging things into the shared branch, but we would sometimes stomp on each other's code nonetheless, often introducing bugs in the process. One time, my co-worker undid two weeks of my work (side note: NEVER `git push --force`) and I had to track it down using `git reflog`. Finally, after a couple serious bugs were introduced that could easily have been avoided had we been using pull requests, we decided to introduce them into our development process.

### How Pull Requests Help
Pull requests are a barrier to getting your code into the shared code base. In open-source projects, someone who merges in a pull request with crappy code is the party responsible for breaking things, not the person who wrote the crappy code.

When I'm working on a feature, I work on a private branch and when that feature is complete, I submit a pull request for it to be merged back into whatever shared strand I branched from. This is an excellent opportunity for a code review. We use the pull request as an avenue to discuss code refactors, catch errors in logic, point out enhancements, and even do QA. At one point, I pull requested a bug fix and used it as an opportunity to ask for help on improving the efficiency of a SQL query.

The first thing I do when creating a pull request is write a helpful description explaining what changes are included, what trade-offs I made, and why I made them. Then I assign the pull request to someone who knows the part of the code base I modified. That person is responsible for making sure that it's logically sound and that it doesn't break things. If it looks good, they'll merge it in. If it needs another set of eyes, perhaps from someone with different domain expertise, they'll re-assign it to someone else.

If the code has problems, they'll comment on them and send it back to me to fix. Any additional commits I push to the same branch are then added to the pull request auto-magically by Github. If the problems are really serious, I may even close the pull request and submit a new one when the feature is fixed.

The additional benefit of this process is that it keeps your team in the loop about what's going on. For this reason, I highly recommend making sure everyone gets an email when a pull request is submitted. Even if someone's not directly involved with a feature, they may have some valuable insight. Or maybe they just enjoy knowing what improvements are coming to the project.

The last advantage of pull requests I want to highlight is that they provide a chance for you as a team to hold each other to a high standard for those best practices that developers often ignore when they're moving at breakneck speed. By doing so, you can maintain a readable and useful commit history (and code base). In particular, we try (often unsuccessfully) to call each other out if we see commits that are not suitably descriptive, code that doesn't have enough comments, or functions that are lacking unit or functional tests. While it sucks to slow down the merger of an awesome new feature, it pays huge dividends down the line when you're trying to debug someone else's code or a test catches a case you forgot to consider.

Not everyone I work with agrees with me, but because of these benefits I submit a pull request for more-or-less everything. Often it's the simplest changes that introduce the most nefarious bugs. Having a second set of eyes is incredibly helpful in avoiding such pitfalls.

### Anticipated Questions
**Q:** A few of us are collaborating on a feature. How are we supposed to work together on a "private" branch?

**A:** In this case, you should treat the feature branch as a shared strand and branch off of it to make your changes. Then when you're ready, submit a pull request into the feature branch!

**Q:** If there are changes to the shared strand between when I branch and when I finish my feature, won't there be merge conflicts that could introduce bugs?

**A:** Absolutely. One way to alleviate this is to rebase your branch onto the shared strand throughout the development process. Rebasing can be painful if there have been a lot of changes so make sure to do it frequently! Another option is to merge the shared strand into your branch prior to submitting the pull request. This allows you to resolve the conflicts and make sure everything works as expected. It'll be harder for your code reviewer to know how to resolve the conflicts than it is for you.

### Acknowledgments, Qualifications and Additional Resources
The ideas presented here reflect the workflow that I've picked up over the past year or so. It works well for me, but I am by no means an expert with git and I'm certain that other people have great suggestions for how to improve on this. If you have any comments, please let me know! I'm eager to improve what I'm doing and learn new tricks. Thanks to everyone who has helped me refine this workflow over the past year (particularly Patrick Yeon), and to anyone who gave me feedback on this prior to sending it out.

I also want to highlight [this great article](http://nvie.com/posts/a-successful-git-branching-model/) that has really helped me structure my thinking about branching and merging.

Finally, a huge qualifer is that having now moving from Romotive to Optimizely I'm being exposed to a whole different set of pull request goals and priorities. I'm going to write another post on this topic once I've had more time to think about the differences.