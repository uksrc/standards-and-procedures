Requirements for Collaborative Development 
===========================================

The general expectation for us to be able to work as a collaborative
team is that any individual should be able to clone a GitHub/GitLab 
repository and be in a position to make meaningful contributions with minimal effort. This is to be achieved by using the principles below;

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
  * The branch should have a "[draft PR](https://github.blog/news-insights/product-news/introducing-draft-pull-requests/)" created against it early to make it clear that the work is in progress
  * the branch should be pushed "regularly"
  * once the work is ready for integration the draft PR should be changed to a "full" PR.

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