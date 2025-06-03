# Code review guidelines

Conducting code reviews provides several benefits:

* It can mitigate the risk of bugs entering the production environment.
* It aids in maintaining consistency with agreed-upon standards and the rest of
  the code base.
* It ensures that the proposed changes meet actual needs.
* It disseminates both project-specific and general engineering knowledge
  throughout the team.
* It offers psychological motivation for engineers to produce high-quality
  output, knowing their code will undergo review.
* It encourages the thoughtful organization of changes into commits.

There are costs of the process as well:

* The process can delay the introduction of changes into the master branch.
* It requires additional time investment from both the reviewer and the
  developer.

To maximize the benefits and minimize the costs, let us stick to following
guidelines: 

# Submitting a merge request for a review 

* Aim to keep the merge request (MR) as concise as possible, limiting the scope
  to the minimum necessary.
    * Aim for 1 - 100 lines of change as an optimal range, with 300 as a
      reasonable maximum. This is a guideline, not a hard-and-fast rule,
      intended to enhance the efficacy of code reviews.
    * Small refactorings may be included. Larger refactorings should ideally be
      handled in a separate MR.
* Ensure that each MR includes a description explaining the motivation for the
  change, or a link to a used project management record (bug report, ticket,
  issue…) containing this information.
* Test all applicable units, maintain up-to-date documentation, and remove dead
  code.
* Consider leveraging automation tools to the maximum extent applicable for your
  project. You may already have unit tests, linting, and style checkers
  incorporated into your CI pipeline, or you might consider adding them if it's
  beneficial for your use case. All these checks should have passed before you
  ask for manual review.
    * Suggestions for additional automated quality checks that could improve
      your workflow are always worth considering.
* The change shall be rebased on top of the latest main/master branch.
* Structure your changes into a sensible number of descriptively-named commits.
  Interactive rebase can be a helpful tool in this process.
* The recommended format is [conventional commits
  v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/). See examples given
  there.
* There shoudl be Defintion of Done document, that specifies what is expected
  from the contribution.

# Choosing a Reviewer 

While a senior developer may offer higher quality review, a junior reviewer can
benefit from the knowledge transfer. The MR submitter should determine the best
reviewer: 

* If the MR modifies existing code, the original code author may be the most
  suitable reviewer.
* If there is an expert in the technology being used, they may be a good choice.
* If someone has expressed interest in learning about the technology used or
  understanding a specific concept or pattern applied, they might be a suitable
  choice.
* Rotate reviewers to distribute knowledge evenly within the team.
* For high-impact code changes, don't hesitate to involve multiple reviewers.
* Avoid asking "anyone" to be the reviewer. It's better to specify who you want
  to review your code. 

# During the Review

## Reviewer's guidelines

* Begin review as soon as possible. Respond promptly and approve the changes
  once satisfied. Reviews should ideally be completed by the following work day. 
* Refrain from nitpicking. Distinguish between blocking issues and suggestions
  in your comments.
* Understand the motivation for the change and ensure it fulfills the intended
  purpose.
* For larger changes, consider checking out the branch locally for a more
  detailed examination.
* Any modifications made to the branch should reset approvals. 

## Submitter's guidelines

* Respond to comments and push resolved issues to the server promptly to keep
  the review process flowing.

# Approving and merging the Merge Request

* Once satisfied, reviewer shoudl explicitly approve the MR.
* Original author of the MR should merge the change after all approvals,
  he is in the position to know that all is ready to be merged.

# Sources 

[Clément Mihailescu, Code Review Best Practices For Software Engineers,
youtube.com](https://www.youtube.com/watch?v=1Ge__2Yx_XQ)

Submitting small changes (10 - 100 lines max), describe the motivation for the
change. Reviewer should be specific: comments that are a matter of opinion
should be stating so. Approve explicitly. 

Amazing Code Reviews: Creating a Superhero Collective • Alejandro Lujan • GOTO
2019 The most important advice: KISS: Keep it small and simple (up to 200 lines,
300 lines absolute maximum, working very hard to break it down). Use We in
wording of suggestions. Offer positive feedback.

[8 CI/CD Best Practices for Your DevOps Journey, Cordny Nederkoorn,
CloudBees](https://www.cloudbees.com/blog/8-cicd-best-practices-your-devops-journey)

“However, to make the most of GitOps, developers are expected to commit directly
to the main branch or merge changes from their local branches at least once a
day. This will force developers to deal with smaller, bite-size bits of
integration pain instead of the massive integration pain (and associated rework)
that happens when attempting to merge many branches into the trunk just before
release.”

[Code Review Tips (How I Review Code as a Staff Software Engineer), Cody Engel,
youtube.com](https://www.youtube.com/watch?v=Y9sp8gONv9M)

Care about description, both sides. Offer positive feedback as well. Make clear
what is blocking the approval and what is optional. Checkout large changes and
try them. You should understand the change. 

[Code Review Best Practices, JetBrains,
youtube.com](https://www.youtube.com/watch?v=a9_0UUUNt-Y)

Names should not lie. We are harder on the code of others than on ours.
Submitter should test it and state so in the description. Be careful what is a
potential problem and what is just an opinion. Gatekeeping review vs. Early
feedback review. Nitpicking is bad, tiny things should be automated. It should
be clear what is expected from the reviewer. Submitter should be respectful to
the reviewer: it should be described, tested, and small. Reviewers should then
do review asap to show respect as well. Motivation: assure code keeps up to
standard, find bugs (not so really useful), share knowledge (highly useful),
make sure the code is useful, make sure the code solves the original problem.
Avoid ping pong reviews! If the design is important, review it early! Make clear
why, who, when and where. Follow up:
https://blog.jetbrains.com/upsource/2015/07/23/what-to-look-for-in-a-code-review/ 

[Giving better code reviews, Joel
Kemp](https://mrjoelkemp.medium.com/giving-better-code-reviews-16109e0fdd36)

“The poor reviewers become known and folks looking for an easy approval know who
to go to. Your team is only as good as your weakest reviewer.” 

“I used to think it was my fault for not being able to understand part of a
diff. It’s not. Hard to reason about code should be corrected.” 

“Giving a valuable code review requires that pull requests are small (&lt;200
lines as a rough gauge). It’s unfair to give a reviewer a diff consisting of
hundreds or thousands of lines of code changes. They’ll end up spending anywhere
up to 30 minutes reviewing that diff and then have to do re-reviews when you
make suggested changes. There’s definitely an inverse correlation between lines
of code and review quality.” 

Catarina Gralha, 9 challenges of managing PRs and how to solve them Excellent
article summarizing a lot of advice I got from asking more experienced
colleagues and consulting sources above. 

“Problem: The more lines of code you need to check, the higher the chance you’ll
overlook something. Plus, developers don’t usually thoroughly review big PRs,
because they are time-consuming and easier to get lost. As such, it’s fair to
say that the bigger the PR, the poorer the code review will be.

Solution: Make smaller and self-contained Pull Requests. Because the PRs are
small, it’s easier for reviewers to understand the context and reason with the
logic, so the review is quicker and more thorough, and the PR is easier to
merge, leading to fewer merge conflicts.” Similar article from the same author.
