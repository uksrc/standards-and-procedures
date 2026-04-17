Requirements for Collaborative Development 
===========================================

The general expectation for us to be able to work as a collaborative
team is that any individual should be able to clone a GitHub/GitLab 
repository and be in a position to make meaningful contributions with minimal effort. This is to be achieved by using the principles below; Being concise, clear, and consistent in our use of tools and processes, and ensuring that the necessary documentation is available to enable a new developer to get up to speed quickly is the overall aim.

## Planning

The team should use the [jira](https://uksrc.atlassian.net/jira/software/projects/TRD/summary) to plan work - work is based on creating "features" which might be of variable size, but should be small enough to be completed in a reasonable time frame (e.g. a couple of weeks).
 The feature will be implemented in a single branch and PR, by a single individual. The initial planning of the feature also tries to roughly size it, however if it becomes clear during implementation that the work is substantially more than expected, then the feature can be split. It is especially useful if the split can be done in a way that another developer can take on the second part of the work, but this is not a requirement. 
The feature can be split by creating a new feature in jira and linking it to the original feature, and then moving the relevant work from the original feature to the new feature. 
The original feature can then be closed once the work that was moved to the new feature is completed.
 The aim is to keep the planning process as simple as possible, and to avoid the "over-planning" that can occur when trying to split work into too many small tasks at planning time.

This means that planning for a feature is recorded in Jira, and the implementation of the feature is recorded in the git commit history and the PR description. This allows for a clear separation of concerns between planning and implementation, and allows for a more flexible and agile approach to development. It is still permissible to create "issues" in github for noting a problem or a bug, but these should be linked to the relevant feature in the jira, and the implementation of the fix should be recorded in the git commit history and the PR description as well.

In the spirit of being agile, any team member is free to create a feature in jira and start working on it, without needing to wait for a formal PI planning meeting - though it should be discussed at a normal standup. This allows for a more flexible and responsive approach to development, and allows for the team to respond quickly to changing requirements or priorities - though it is still expected that the team will have regular PI planning meetings to plan work for the next PI, and to review the work that was done in the previous PI.

### Jira Feature Creation expectations
* https://uksrc.atlassian.net/jira/software/projects/TRD/boards/632/timeline
   * The feature should be created in the relevant epic from the timeline view - this can be done by pressing "+" when hovering over the relevant epic in the timeline view. This ensures that the feature is automatically linked to the epic.
* The feature should have a clear and concise title that describes the work to be done
* The feature should have a clear and concise description that gives an overview of the work to be done, and any relevant context or background information
* The feature should have a clear definition of done that describes what needs to be done for the feature to be considered complete.
* The feature should have an estimate ot the amount of time that it is expected to take to complete the feature in "real" workdays.

### Starting work on a feature
* The feature should be transitioned to "in progress".
* The developer should create a branch in git with the name of the feature (e.g. TRD-1234-feature-name) and start working on the feature in that branch. - this can be done  with the "create branch" feature in jira, which will automatically create the branch with the correct name and link it to the feature in jira. 
* The branch should have a "[draft PR](https://github.blog/news-insights/product-news/introducing-draft-pull-requests/)" created  against it, as soon as possible, to make it clear that the work is in progress for anyone who is just looking from the github end.
* The branch should be pushed "regularly" to github, so that the work is visible to others and so that it is backed up in case of any local data loss failures. This also allows for early feedback from others if they are interested in the work being done.
* The jira feature ticket should be updated at least once a week on Monday to give an update on the progress of the work - this need only be a brief update.

## Git repository 

* On cloning a project it should be buildable with a simple command line
  * **Java** - [gradle](https://docs.gradle.org/current/userguide/getting_started.html) should be used as the build tool - note use [kotlin](https://docs.gradle.org/current/userguide/kotlin_dsl.html) control files for type safety rather than groovy.
  * **Python** TBD
  * **Other** use make to "build" - in particular use [GNU make](https://www.gnu.org/software/make/manual/make.html)
* Projects should contain appropriate unit tests
* Projects should have CI set up to run these tests on PR - using ubuntu as the starting OS.
* The project README should give a brief overview of
  * overall purpose
  * how to start coding
* Contributions to the code should be done on a feature branch with is created along with the jira feature ticket as detailed above.
  * Once the work is ready for integration the draft PR should be changed to a "full" PR.
  * Run a copilot review on the PR to check for any potential issues with the code - this is not a replacement for a human review, but can be a useful tool to catch any potential issues that might have been missed.
  * A human should review the PR also before it is merged.
  
* Repositories should not contain "blog"-style work records of work that was done - this should be in the commit history and the PR description. The commit history should be clean and meaningful, so that it is possible to understand what was done by reading the commit messages and the PR description. Diffs will then only contain the actual code changes and not the "noise" of the "blog" process.



## Developer local Environment

The minimal tools that a developer is expected to have installed are

* git
* JDK 17 (minimum version)
* Docker/Podman as a container running front-end

Individual projects might require more tools, but the CI should make it clear what those are.

## Software Repositories

We have local services for the products of our builds to be published to;

* Java maven artifacts, python wheels, node npm  etc. uses [nexus](https://www.sonatype.com/products/sonatype-nexus-repository) at https://repo.dev.uksrc.org/.
* Container image repository [harbor](https://goharbor.io) at https://images.dev.uksrc.org/
