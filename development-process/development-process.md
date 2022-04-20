# Development Process

We work in an agile environment. We use scrum.&#x20;

[There is a task board per sprint](https://tree.taiga.io/project/jbothma-wazimap-ng/backlog).

Look for the highest priority available task in the current sprint.&#x20;

**If you can't find any available tasks** in the current sprint

1. ask the rest of the team if you can help with anything,&#x20;
2. let the PO and PM know that you can't find anything to work on
3. groom the backlog of upcoming sprints
4. Start working on tasks in the upcoming sprint

**The priority of what to work on** is as follows:

1. data mis-representation bugs and bugs seriously affecting production (these should be moved to the top of the sprint)
2. Deploy something that is Ready to Deploy unless we're waiting for a particular deploy time
3. The story highest up in the sprint that is not finished

### As a Developer

Developers should only work on one task at a time.&#x20;

Once you decide to **start working** on a task, this is your process:

* Assign the task to yourself
* Post in the Slack channel on which issue you‘re starting to work on
* Create a Draft PR (use the `--allow-empty` git command to create an empty commit and push the branch to the repository).&#x20;
* Adjust the description of the PR with a description of the ticket in your own words.
  * Сheck off the item _good description_ in the PR checklist
* Adjust the title of the PR
  * Check off the item _good title_ in the PR checklist
* Create a link to the issue best to use _closes #..._
  * _issue linked_ in the checklist
* On the right side of the PR make sure the PR is linked to a ticket and therefore the GitHub Project _WazimapNG_ is added (otherwise the automation won‘t work).
* Add Design Screenshots (if necessary)
* Start working on the ticket&#x20;

Once you‘re **done working** on the issue follow this process

* Run all tests locally
  * Check off the item _ran tests locally & are passing_ in the checklist
* Run the build (FE `npm run build` & BE `docker-compose up`)
  * check-off _does it work (build) locally_ from the checklist
* Write down how to test your changes locally and add them to the PR (check off the item)
* Go through the Code Quality Checklist
  * make sure you do not commit commented out code
  * Make sure you do not have unnecessary login (console.log, print, etc)
  * Make sure you did not add magic numbers&#x20;
* Fill out the changelog&#x20;
* Do a review yourself
  * Look at the changed files
  * make sure you have not committed anything outside the issue
  * make sure the CI builds are green
  * make sure the items in the checklist are checked-off
* Move the card to _Needs code review_
* Post to slack that you finished the task and link the PR

## Common broken assumptions

These are things we've seen cause bugs when we didn't consider them. We should try and have them in mind when implementing and writing tests for anything on this project.

* Data can exist for some geographies in a set of siblings but not all
* An admin can configure a default filter value which doesn't exist in the data for a given geography
