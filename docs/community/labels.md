# Labels

We use very specific labels to help categorise our issues. This page explains what each label means.

## Contribution Labels

These are the most important. These labels indicate who is encouraged to make a pull request to resolve the issue.

| Label              | Explanation                                                                                                                                                                                                                                                      |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `good first issue` | An issue with this label is intended for contributors who are brand new to the project. These issues should not require prior knowledge of the codebase, and the conversation on the issue will include a detailed description of how to implement a resolution. |
| `help wanted`      | These issues are open for contribution from anyone who is interested. The conversation may not include a detailed description, as these issues typically assume you have prior experience with the codebase.                                                     |
| `🔒 staff only`    | These issues require specific access to the production infrastructure to test properly. These are restricted to project maintainers/staff for that reason.                                                                                                       |

## Aspect Labels

These labels indicate the scope of the work required to resolve the issue.

| Label                 | Explanation                                                                                                                                                                                  |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `💻 aspect: code`     | This is the most common. These issues require work on the project's code-base.                                                                                                               |
| `🤖 aspect: dx`       | These issues typically require changes to the project's tooling, such as automated tests, development dependencies, etc.                                                                     |
| `🕹 aspect: interface` | These issues might require code changes, but these are specifically things that require changing the end-user's experience. This might be something like CSS changes, or replacing an image. |
| `📄 aspect: text`     | These issues are related to a project's documentation. These don't require code changes, but might require markdown experience as most of our documentation is written in markdown.          |

## Goal Labels

These labels indicate the goal of the issue. Our projects tend to follow a specific modular approach, and these labels help indicate the type of changes you might be making.

| Label                  | Explanation                                                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `⭐ goal: addition`    | These issues add a new feature to the project. Typically, this means you're adding a new code file from scratch, following the project's style.   |
| `🛠 goal: fix`          | These issues fix a bug in the project. Typically, this means you're editing existing code within existing files.                                  |
| `✨ goal: improvement` | These issues expand upon an existing feature. Typically, this means you're adding code to an existing file, but not necessarily adding new files. |

## Priority Labels

The priority labels indicate the importance we've assigned to a specific issue. The higher the priority, the more of a focus it is for our team.

| Label                   | Explanation                                                                                                                                                             |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `🟥 priority: critical` | These issues are typically show-stoppers. This label is reserved for issues which need immediate attention because the project is **unusable** until they are resolved. |
| `🟧 priority: high`     | This label applies to issues that aren't preventing the project from being _functional_, but are preventing further development until they're resolved.                 |
| `🟨 priority: medium`   | Medium priority issues are things that we want resolved as soon as possible, but they aren't preventing other development from occurring.                               |
| `🟩 priority: low`      | This is probably the most common label. This is for issues that we'd like resolved, but aren't considered as things we want done ASAP.                                  |
| `🟪 priority: none`     | This label indicates an issue that would be nice to have resolved, but isn't essential enough to dedicate maintainer time to fixing.                                    |

## Status Labels

Status labels allow you to see where a ticket is at in the lifecycle of the project.

| Label                             | Explanation                                                                                                                                                                                                                                                                             |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `🚦 status: awaiting triage`      | This is the most common status label. This label is automatically applied to new issues, and indicates that the maintainer team has not reviewed and responded to the issue. You are still welcome to share your thoughts, but these issues have not received any maintainer attention. |
| `🚧 status: blocked`              | This label is applied to issues that might have a planned resolution, but that resolution depends on a separate issue being resolved. These aren't ready for work **yet**, but will be soon.                                                                                            |
| `⛔️ status: discarded`           | This label applies to an issue that we don't intend to resolve. Typically, this is on feature requests that aren't in line with the project's goals.                                                                                                                                    |
| `🙅 status: discontinued`         | We rarely use this label, but this applies to feature request issues on projects that are solely in maintenance mode - that is, projects we aren't adding new features to but are still supporting and providing bug fixes for.                                                         |
| `🏷 status: label work required`   | This applies to an issue that might have some discussion on it, but hasn't been appropriately labelled and categorised.                                                                                                                                                                 |
| `🏁 status: ready for dev`        | These issues are ready for contribution. If a contributor is assigned, they have indicated interest in working on the issue and we encourage you to collaborate. This pairs with the Contribution Labels listed above.                                                                  |
| `🧹 status: ticket work required` | This label indicates that the issue does not have enough information for proper triage. Typically, this pairs with the Conversation Labels listed below.                                                                                                                                |

## Conversation Labels

These labels indicate that the issue has received initial maintainer attention, but is waiting on more information from the author or the maintainer team.

| Label                 | Explanation                                                                                          |
| --------------------- | ---------------------------------------------------------------------------------------------------- |
| `💬 talk: discussion` | This issue is being actively discussed, but has not been accepted as something we intend to resolve. |
| `❓ talk: question`   | These issues are waiting on additional information from the author in order to triage properly.      |

## Special Labels

These labels are specifically used for unique events.

| Label                    | Explanation                                                                                                                                              |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Hacktoberfest`          | This issue is indicated as a valid contribution opportunity for Hacktoberfest.                                                                           |
| `hacktoberfest-accepted` | This is used to label pull requests which are valid Hacktoberfest contributions, but might not be merged in time for the event.                          |
| `invalid`                | This label is specifically used on pull requests which were made with the goal of spamming Hacktoberfest contributions, and were not made in good faith. |

## Pull Request Labels

We have automation that applies specific labels to our pull requests.

| Label                       | Explanation                                                                                                |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `✅ pull: accepted`         | This pull request has been merged into the code base.                                                      |
| `⚠️ pull: merge conflict`   | This pull request has conflicts with the target branch. Those need to be resolved before we can review it. |
| `🔍 pull: ready for review` | This pull request is not in draft mode and is waiting for maintainer review.                               |
| `❌ pull: rejected`         | This pull request was not accepted by maintainers and was closed.                                          |
| `⏫ pull: requires update`  | This pull request has had changes requested by the maintainer team.                                        |
| `⚒️ pull: work in progress` | This pull request is in draft mode and is not ready for review.                                            |
