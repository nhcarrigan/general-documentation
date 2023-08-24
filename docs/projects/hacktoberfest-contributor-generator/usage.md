# Usage

This is a Node.js tool to generate a list of GitHub users who made valid contributions to a project for Hacktoberfest. The list will be sorted by number of contributions, and will provide a formatted Markdown document with the list of contributors.

## How to Use

This project is intended to run locally. Start by cloning the project, switching to your project directory, and running `npm ci` to install the dependencies.

Then, `cp sample.env .env` (or copy manually) to get the environment variable file. You will need to set three values:

- `GH_TOKEN`: This is a [GitHub API Token](https://github.com/settings/tokens). While this is not _technically_ required to use the API to view public pull requests, it is required for private repositories, provides higher rate limits, and is generally polite API use.
- `OWNER`: This is the owner for the repository you wish to query. This should be the user or organization name.
- `REPO`: This is the name of the repository you wish to query.

When you have everything set up, run `npm run build` to compile the TypeScript into JavaScript, then `npm run start` to launch the process!

You will see some output in the terminal - the script will check if the repository has the `hacktoberfest` topic, will query PRs that were created after the event started, and will check each PR against the logic that determines if a contribution is valid. Once this list is compiled, the process will create a `results` directory and save your list to a `owner/repo` Markdown file.

## Logging

The results of a run will also be written to `/results/_runLog.log` so you can audit any excluded PRs if needed. Note that this is a running log, which means if you run this script more than once each run will be appended to the file.

For convenience, runs are broken up by `==RUN BEGIN==` and `==RUN END==`.
