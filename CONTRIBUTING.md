# Contributing
This document is centralized in the pybugreports repository for convenience, but applies to all repositories within the pyanodon organization.

## Pull requests
Maintaining the full mod set is a considerable effort and we owe a lot of thanks to the community contributors who help make this happen. If you wish to write and submit changes, please make sure you follow the guidelines below.

For information on the project layout, setting up your environment, etc., please see the [docs](https://pyanodon.github.io/pybugreports/).

### Before writing code for submission:
- If you're considering a large feature, refactor, or re-organization, please [ask](https://github.com/pyanodon/pybugreports/issues/new) first. Not doing so risks putting a large amount of work into something that may be rejected, and—if your project has been considered or attempted before—there may be good advice on pitfalls to avoid along the way.
- If you're considering a balance change, please [ask](https://github.com/pyanodon/pybugreports/issues/new) first. Balance is opinionated, and unsolicited pull requests with balance changes will receive heavy skepticism.
    - Balance changes and bug fixes that break existing production lines should be based on and target the `breaking-changes` branch.
- Please familarise yourself with the license used by the project and understand that, by submitting a pull request, you allow the project to license your work under those terms.

### When writing code for submission:
- Follow the coding conventions already present in the project, including style, indentation, and file structure.
- Limit your commits to relevant changes with concise messages. You are welcome to submit a [draft](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests) that doesn't meet this requirement, but please clean it up before marking it as ready for review.
- Be aware that pull requests containing content written by generative AI (ChatGPT, Copilot, Gemini, etc.) or machine translation (Google Translate, DeepL, etc.) tools will not be accepted.

### When submitting a pull request:
- Give your pull request a descriptive title - "fix crash from ABC when clicking XYZ" is a useful summary that doesn't require opening the pull request to understand, "fix crash" is not.
- Link to any bug reports that your changes address.
- If you are making changes to multiple project repositories, link to the companion pull requests.
- Be patient with review comments, if any are provided. Comments asking "why" for code logic are not necessarily requesting changes, but seeking to understand your approach.