Requirements for Collaborative Development 
===========================================

The general expectation for us to be able to work as a collaborative
team is that any individual should be able to clone a GitHub/GitLab 
repository and be in a position to make meaningful contributions with minimal effort. This is to be achieved by using the principles below; Being concise, clear, and consistent in our use of tools and processes, and ensuring that the necessary documentation is available to enable a new developer to get up to speed quickly is the overall aim.

## Planning

The team should use the [jira](https://uksrc.atlassian.net/jira/software/projects/TRD/summary) to plan work - work is based on creating "features" which might be of variable size, but should be small enough to be completed in a reasonable time frame (e.g. a couple of weeks).
The feature will be implemented in a single branch and PR, by a single individual. No attempt will be made to split the feature into multiple tasks at planning time, but if whilst implementing the feature it becomes clear that there is more work than expected, then the feature can be split into multiple features in the jira and the branch can be split into multiple branches as necessary. The aim is to keep the planning process as simple as possible, and to avoid the "over-planning" that can occur when trying to split work into too many small tasks at planning time.


## Git repository 

* on cloning a project it should be buildable with a simple command line
  * **Java** - [gradle](https://docs.gradle.org/current/userguide/getting_started.html) should be used as the build tool - note use [kotlin](https://docs.gradle.org/current/userguide/kotlin_dsl.html) control files for type safety rather than groovy.
  * **Python** TBD
  * **Other** use make to "build" - in particular use [GNU make](https://www.gnu.org/software/make/manual/make.html)
* projects should contain appropriate unit tests
* projects should have CI set up to run these tests on PR - using ubuntu as the starting OS.
* The project README should give a brief overview of
  * overall purpose
  * how to start coding
* contributions to the code should be done on a feature branch if the work is expected to last more than a day
  * in addition a feature should be created in the team jira https://uksrc.atlassian.net/jira/software/projects/TRD/summary that describes the work to be done and the branch should be named with the jira issue number as a prefix (e.g TRD-1234-branch-name) - this means that it will be automatically linked in the jira issue and the PR will be automatically linked when it is created.
  * The branch should have a "[draft PR](https://github.blog/news-insights/product-news/introducing-draft-pull-requests/)" created against it early to make it clear that the work is in progress
  * the branch should be pushed "regularly"
  * once the work is ready for integration the draft PR should be changed to a "full" PR.
* repositories should not contain "blog"-style work records of work that was done - this should be in the commit history and the PR description. The commit history should be clean and meaningful, so that it is possible to understand what was done by reading the commit messages and the PR description. Diffs will then only contain the actual code changes and not the "noise" of the "blog" process.



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
