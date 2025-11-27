**CI/CD Versioning Policy**

1.  **Purpose**
  
    To define the guidelines for using CI/CD across UKSRC projects. The aim is to enable quality-ensuring Zrocesses to ensure reliable and measurable deployments.


2.  **Scope**

    This document applies to all projects developed by UKSRC that are intended to be deployed as a service within the UKSRC infrastructure. This includes, but is not limited to:

    - Container images built for deployment within UKSRC-managed Kubernetes clusters or supporting systems.

    - Libraries, packages, or shared components that are published to and consumed from UKSRC-hosted registries.
    
    - Projects hosted in the UKSRC GitHub organisation and any associated repositories under UKSRC administration.

    - Services or tools deployed internally to support, extend, or automate the UKSRC platform or operational infrastructure.

3.  **Configuration**

    UKSRC projects follow a standard branching model:

    - **Main branch** -- protected; all changes must be submitted via a pull request.

    - **Feature branches** -- created for work on individual features, tasks, or bug fixes, and merged into the main branch through a reviewed pull request.

4.  **Prerequisites**

    Actions Required before submission and tagging.

    - *Lint*, use the most appropriate tool for the language. Resolve as many issues as possible, issues such as "typo" warnings for domain related acronyms etc. are understandable.

    - *Unit tests* -- All unit tests must pass as they will be run as part of the integration process.

5.  **Versioning/Tagging**

    5.1.  **Semantic versioning**
    
    The tag's actual release number will be made up of three numbers to represent the version iterations. An example of '*1.1.0*' would be defined as follows:
    >
    > *1.1.0* -- {*Incompatible changes*}.{*Backwards compatible new features*}.{*backwards compatible bug fixes*} *
    >
    > *Major. Minor. Patch -- 1.1.0

    **Major** -- increased for incompatible or breaking changes

    **Minor** -- increased for backwards-compatible new features

    **Patch** -- increased for backwards-compatible bug fixes

    5.2.  **Potential tags**

    > *1.2.0-snapshot* - Manual deployment to our Nexus repository.
    >
    >  *1.2.0-rc1* - Deploy to development/staging
    >
    >  *1.2.0-rc2*
    >
    >  *1.2.0* - Main branch - Deploy to production
  

    Tags used on the *main branch* only (*other than snapshots*) to notify the CI/CD pipeline for the *rc* (release candidate) and *release* tags.

    **Version**

    **Semantic numbering signifies version**

    The numbers 1.2.0 as *major. minor. patch* represents the actual version number.

    ***State Qualifiers***

    *Semantic versioned tag such as '1.3.1'* (*and/or -rc1','-rc2', etc*) or '*snapshot'* declares the state of commit at the tag.


6.  **Continuous Integration**

    The CI/CD mechanism will only function from the *main* branch and will require a tag with one of the specified state qualifiers to be handled by the CI/CD tools. The only exception to this would be a *snapshot* release mainly intended for feature branches. Snapshots are mainly used for development/test releases that are intended to be non-permanent (mainly used by Java/Maven/Gradle).
  
    6.1.  **Responsibilities**

    - Build the project/component

    - Automated testing (unit and/or integration tests)

7.  **Continuous Deployment**

    - Deployments will only occur if there is a nominated destination.

    - Only from tagged releases.

    - Only on the main branch for a release or a snapshot on a feature branch.

    - Only from tagged releases.

    7.1.  **Environments**

    - Development

    - Production

**Further:**

  CI -- Linting, static analysis? -- see Prerequisites

Integration testing -- See Ben Green's document regarding Playwright
(link when published)

**Notes:**

Snapshots for manual non-CD releases, only to be uploaded to our nexus
due to maven repository expiration. <https://repo.dev.uksrc.org/>
(credentials -- see Redmine)
