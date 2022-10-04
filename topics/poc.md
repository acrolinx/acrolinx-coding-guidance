# Proof of Concept

The goal of a proof of concept (PoC) is to demonstrate whether a product idea can be turned into reality.
A PoC should aim to reduce risk and help you understand the effort of project.
It's usually a good idea to start a new development project with a PoC.

## Questions To Answer

* Is the idea viable?
* Which features are feasible?
* Which technology can you use?
* What's the best technology for the environment?
* What's the minimum viable product to deliver in the next phase?
* Where and how should you integrate?

## Best Practices

* Doing a PoC usually takes from 2 hours up to 2 days.
* If you can do something quickly and properly, then do it the proper way during the PoC.
    - Do you need a place to store your code? [Create a repo.](project-setup.md#git)
    - Do you have to build a package? [Create a proper package.](packaging.md)
    - Have you figured out how to build, debug, or install? [Document it in the Readme.md.](project-setup.md#readme)
* The goal of a PoC isn't to finish the integration, so don't get stuck on solving problems.
  The main goal is to determine the overall feasibility and identify problems and potential solutions.
* Recognize when your PoC is finished. Once you reach this point, create separate tickets.
  Getting organized makes it easier to track and test your work.
  It also simplifies the life of the project manager and developers who join the project later on.
* While doing a PoC, it's OK to have a lower level of [code quality](coding-style.md).
  Don't forget to document your technical debt so you can clean things up when you start the project.
  Again, using a ticket might be a good idea.
* Sometimes just looking at the APIs of an application is sufficient for a PoC.
  In this case, you don't have to try things out if you're 100% sure it'll work.

## Proof of Concept Template

Use the [proof of concept template](poc-template.md) for documenting your findings in a standardized way.
