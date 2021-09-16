# Code Review Process

Your code will be reviewed. And you can can take steps to make it easier for the reviewer and yourself.

## What is the job of the Review?

The review is there to improve the code quality and to ensure architectural direction and correctness. 

The big benefit of a review is to help you get better. You will learn from Code Reviews.

Everybody's code can be improved. And your code will get better with reviews. Programming is a skill that improves with training.

Code Reviews help reveal implicit knowledge that is not expressed in code.

Four eyes see more than just two. Even the best testing does not lead to 100% bug-free code. It helps, but Code Reviews are a big part of providing confidence in the code.

## Who can/should approve a PR

Everyone can submit their review and we encourage everyone to do so. But only the PM and the Lead Developers can approve a PR. 

### Who can merge a PR?

Once the PR is approved anyone can merge the PR. And you are encouraged to merge the PR once it is approved. 

## How to create a good PR

Create a PR as early as possible, and push frequently.

### Open a Pull Request \(PR\) once you decide to work on an issue.

Use the `--allow-empty` flag with git to create an empty commit and push it to create a PR. Use the branch naming as described in the git handbook.

Create a Draft Pull Request to signal, this is a work in progress. Change to Ready to review once you're confident that it's ready to be reviewed.

If you share your progress early on, the reviewer can take a glance at your work early, and help you move in the right direction.

### Use the PR template

The template is there to help you and the reviewer to make the process as easy and fast as possible. 

### Write a good description

The description should reference the issue that the PR is addressing. It should include, in your own words, what you are trying to accomplish. How you understand the issue. It will help the issue creator and the reviewer to better understand and address potential misunderstandings early on.

The description should also include your thinking process. How do you approach this issue. 

And It should include how you went about testing this locally. For the frontend which buttons to click on which pages, for the backend which API endpoint to call and how.

As well as anything you’d like the reviewers opinion on specifically \(eg class names, time complexity of code, etc\)

### Run quality checks locally

Run codeclimate locally and address issues early on. It will show you issues that will be raised once you push the code. 

### Run the tests locally

Make sure you run the tests locally \(no need to run E2E\) to make sure they pass.

### Only mark the PR to ready for review, when you truly think it's ready

Don't mark it ready too soon, when you still working on it or did not push the latest changes. Take a look if the code diff looks like you would expect.

### Leave your own review

If you wanna be proactive leave your own review and comment on the lines that you think might be worth explaining to the reviewer. You will also find issues you didn't notice while you were coding when you take a reviewer perspective.

djfldsjfdjfdfkdsl

* read through story - what's the point of the change?
* read through PR description
  * what change is the dev trying to make?
  * what tests does this rely on to keep working? which ones are new?
* run the tests - do the tests actually pass?
* review the code
  * Does the code fit in with the context?
  * Is the code of sufficient quality?
  * Does anything look scary? Risky?
  * Does anything not look right?
  * Does it solve the problem sufficiently generally or is it too specific?
  * Have we considered the
* resolve conflicts if possible
* approve

More QA

* For all the different sorts of data, will this work?
* For all the different sorts of silly things users and admins can do, will this work?

PO review process

* Does it address the business problem?

