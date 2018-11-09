# PoC - Proof of Concept

The idea of a proof of concept is to ensure that a project is feasible.
It should reduce the risk and give an understanding of the effort.
Typically it's a good idea to start a new project doing a PoC.

## Questions That Should Be Answered

* Is it feasible at all?
* Which features are feasible?
* Which technologies can be used?
* What's the best technologies for the environment?
* What's the minimum viable product?

## Essence of a PoC

* The elaboration usually takes 2 hours up to 2 days.
* If there's something that doesn't take longer to do it the proper way, don't hesitate to do it the proper way.
  You need a place to store your code? [Create a repo.](project-setup.md#git) You have to build a package?
  [Create a proper package.](packaging.md) You've figured out how to build, debug, or install? [Document it in the Readme.md.](project-setup.md#readme)
* The goal of a PoC isn't to finish the integration. Don't focus and get suck on solving problems.
  The main goal is to identify problems, solutions, and the feasibility at all. Recognize when you PoC is finished.
* Once you reach this point, create separate tickets. It makes it easier to track and QA the work.
  It also simplifies the life of the project management, and developers starting and driving the project later on.
* It's OK to have a lower [code quality](coding-style.md) while developing a PoC.
  Don't forget to document your technical debt and nice it up, once you start the project.
  Again, using ticket might be a good idea.
* Sometimes it's already enough to look at the APIs.
  In this case, you don't have to try things out, if you're 100% sure it'll work.

## Proof of Concept Template

Please use the [proof of concept template](poc-template.md) for documenting your findings in a standardized way.