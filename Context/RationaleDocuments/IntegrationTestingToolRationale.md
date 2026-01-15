# INTERGRATION TESTING
There are unsurprisingly a number of options that present when looking
for integration testing tools.

By integration tests, we are seeking a tool set that enables the smooth
hand off of information between associated but uncoupled modules. In the
UKSRC Data Archive service, we are specifically referring to the backend - such as calls to a TAP service (or indeed any API) - and front end - a React based UI system. On face value the available frameworks may seem to be UI focused unit testing tools. This isn't the case; unit tests are different because they only focus on the isolated internal functioning of a module. In this respect test plans should concentrate on the collective functioning of modules, including behaviours such as
data entry, workflow progression, form population etc. The conclusions of this evaluation are agnostic to unit testing and should not be understood to be suggesting the replacement of any existing unit tests.

# Criteria
The tooling choice will be based on support for the following
requirements:
1.  work with Java, TypeScript/JavaScript, and ideally Python
2.  work in common browsers: Firefox, Chrome, Safari and Edge
3.  be consistent with whatever team Mango is using for Science Gateway
4.  work with GitHub Actions

# Methodology
Throughout this process I reached out to my wider network to garner
opinions from software professionals. These include friends and former
colleagues from other companies or departments from within UoM. Notably
I also consulted a key figure from SRCnet Mango (Science Gateway) team
to understand what is being used there.

I have done an extensive google, stack overflow, reddit and YouTube
search. Several options emerged quickly, two of which I was aware of
(Cypress and Selenium), several more I wasn't I had no prior knowledge
of.

With initial thoughts beginning to develop I moved over to ChatGPT
specifying the purpose of the tooling I was looking for and listing the
most common frameworks from the search stage of my process. The results
of ChatGPT (model 5.0) were consistent with the four candidates that I
had on my initial long list: Cypress, Playwright, Puppeteer, and
Selenium. It's suggestion was to drop Puppeteer as it deemed it the
least capable for our scenario. Based on the summary feature lists that
I had seen, I was satisfied that the remaining candidates were capable
options and so began the final selection process.

The final part of the process was to take three tutorials (via LinkedIn
Learning), one for each of the remaining candidates. This gave me an 'in
use' understanding of each.

# Candidates
Here follows a high-level summary of the key point on each candidate
### Cypress
Cypress uses browsers installed on the host system to run its test; this
can be seen as both positive and negative. On the one hand you can test
against specific browser versions seeing the actual result; On the
other, tests are less stable and are sometimes dependent on environment
set up. and Test syntax is fairly simple, and it looks pretty good to
get going straight away.

There is support for GitHub actions via 'cypress-io/GitHub-action' -
<https://github.com/cypress-io/github-action>. It is in active
development though and is specifically pointed to from the Cypress.io
website, so is officially supported. The setup is easy though not as
easy as other alternatives.

The default setup seems to cover most of scenarios, but configuration
can be applied to modify default behaviours. Cypress appears to have the
simplest unboxing process when starting out but seems significantly more
limited in comparison to other options.

Cypress has a comparatively small number of supported languages (for
writing the tests) - it only supports JavaScript (and typescript). It
also supports fewer browsers than alternatives - Chrome, Edge, and
Electron. A decent portion of our userbase will be using Safari and/or
Firefox making Cypress something of an incomplete solution.

### Playwright
Playwright uses a fixed, known set of browsers whose versions are bound
to the playwright release version. This is the opposite case to Cypress
and the pros/cons of such are similarly opposed; fixed browser versions
might be more limiting for new features or version specific quirks but
being inbuilt in the tooling they are not subject to the environment and
allow an expanded set of tools to be available to the framework.\
I have found good evidence notably smooth interactions with GitHub
Actions. The initialisation process offers a GitHub Action generation
step and there is an official GitHub Action maintained by Microsoft -
<https://github.com/microsoft/playwright-github-action>.

Configuration seems flexible, with more upfront work required by the
user. This seems like a plus as any instance will be built on fewer
assumptions.

Playwright has broad language support - TypeScript and JavaScript,
Python, C# and Java. It has an equally inclusive browser support
profile, Chromium, Chrome, Edge, Firefox, and Webkit/Safari. Both
programmers and users will be well supported with this tooling. It runs
fast, though how much of a benefit this will be in the short term is
unclear. It is nice to be assured that it can scale in any case.
Playwright is very much the new kid on the framework block and as such
has made headway is solving the common problems of incumbents.

### Selenium
Selenium is very much the aging silverback. It is an incumbent of 20 or
so years. Browser support is good, and it is the de facto tool if you
intend to target older versions of Internet Explorer. That said Selenium
is comparatively more complicated to set up, there are additional tools
needed to add modern features -- such as GitHub Actions which require
3rd party tools and has no official support -- and it is acknowledged
as notably slower than alternatives. It is the kind of tool that might
be justifiable with specific cases, or extensive operational knowledge
but has significant drawbacks in comparison to more recent frameworks in
its capability.


|            | Language Support                                                | Browser Support                                                            | Matches Team Mango | GitHub Actions Support                                                                 |
| ---------- | --------------------------------------------------------------- | :------------------------------------------------------------------------- | ------------------ | -------------------------------------------------------------------------------------- |
| Cypress    | JavaScript/TypeScript                                           | Chrome<br>Edge<br>Firefox (unstable)                                       | No Conflict        | -Officially supported project<br>-No generation<br>-Cross browser possible with config |
| Playwright | JavaScript/TypeScript<br>Python<br>C#<br>Java                   | Chrome<br>Edge<br>Firefox<br>Webkit<br>iOS/Android Webkit                  | No Conflict        | -Officially supported project<br>-Generation included<br>-Cross browser inbuilt        |
| Selenium   | JavaScript/TypeScript<br>Python<br>C#<br>Java<br>Kotlin<br>Ruby | Chrome<br>Edge<br>Firefox<br>Safari<br>iOS/Android Webkit (via Appium)<br> | No Conflict        | 3rd party support only                                                                 |

# Decision

Given this search my preliminary decision is to use Playwright. It is
flexible, supports a range of languages and most browsers. It includes
features like supported test generation and parallel execution, it is
cross-browser by default and has a reasonably established support base
and community support continues to grow.

Installation is relatively simple, and it offers GitHub action tie in
from installation.

This decision remains preliminary until we have reached decent test
coverage (say \>50%) or until we learn more about user requirements.
Given the feature set the key challenge to our finalisation of this
decision is if it later becomes necessary to support Internet Explorer
as a core or principal browser. However, in this eventuality, a great
deal more than just our integration testing would need to be modified.
