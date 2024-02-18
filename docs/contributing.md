# Contributing

> [!TIP]
> This document provides a high-level overview of contributing to our projects. Check with each project's documentation for more specific or supplemental instructions, if needed.

Please ensure all pull requests and contributions comply with the [Developer Certificate of Origin](https://developercertificate.org/).

> [!NOTE]
> All contributions to our projects will be licensed under our [global license](/license.md)

## Setting Up Your Code

First, fork the repository to your own account. Then use `git clone <url>` to bring your forked repository down to your local machine (remember to get the URL for _your_ repository, not the original). Optionally, use `git remote add upstream <url>` to add the original repository as the upstream (this is helpful for keeping your fork up-to-date).

## Claiming an Issue

All of our issues are open to contributors! If you see an open issue you would like to work on, please comment on the issue so we may assign it to you.

> [!NOTE]
> Assigned issues that have not had any activity in a week will be unassigned.

If an issue is already assigned, that means someone has expressed interest in working on it. We encourage you to reach out to them and collaborate on a PR together!

We use special labels to help categorise issues. Feel free to [browse our breakdown of the labels](/labels.md).

## Working on your issue

Before starting work, we highly recommend ensuring that your forked version is up to date. If you set the `upstream` as mentioned in [Setting Up Your Code](#setting-up-your-code), run these commands in your terminal (with the terminal pointed at the root directory of your local files):

- `git fetch upstream` - this gets the current state of the original repo, without pulling down the changes to your local machine.
- `git reset --hard upstream/main` - this resets the state of your local files to match the current state of the original repo.
- `git push -f` - this forces the changes to your forked repo (thus making it match the original)

> [!NOTE]
> You will lose any changes you are currently working on. Do this with care.

Next, use `git checkout -b <branchname>` to create a new branch for your work. It's always a good idea to avoid committing changes directly to your `main` branch - this keeps it clean and avoids errors when updating (above).

Branch names should follow a convention of `scope/description` where:

- `scope` is the nature of the changes (eg. `feat` for a new feature, or `docs` for documentation update). This should match the scope of the related issue.
- `description` is a brief description of your changes, such as `update-contribs` for updating the contributing guidelines.

Now you are free to work on your code! When you are satisfied with your changes, you can commit them with `git commit -s -m "message"`, where:

- `-s` flag signs the commit, to verify the connection with your GitHub account.
- `-m` flag sets up the commit message.
- `message` is the commit message: a brief (50 character max) message describing what the commit changes.

> [!TIP]
> If you aren't sure which package manager to use, you can reach out to us in our [chat server](https://chat.nhcarrigan.com).

### Installing Packages

- If the project uses `pnpm`, you should run `pnpm install`.

### Adding Packages

`pnpm install` will allow you to add a new package.

When adding a new package, you should use the `--save-exact` flag to pin the package version. The CI will check for unpinned versions when you open a PR.

If the package is only for development (working on the project), and not needed for production (running the project), you should _also_ use the `--save-dev` flag to add the package to the `devDependencies` section of the `package.json` file.

For example:

```bash
pnpm i --save-dev --save-exact @types/naomi # Adds a dev dependency
pnpm i --save-exact naomi # Adds a production dependency
```

### Oops! I used `npm` when I should have used `pnpm`

No worries! A quick note that if you ran `npm install` or `npm ci`, then `pnpm` will ignore the installed packages. You will need to run the following commands to get back in sync:

```bash
rm -rf package-lock.json node_modules
pnpm install
```

## Testing Changes

> [!NOTE]
> Make sure to follow the steps above to check which package manager the project uses, and use the appropriate commands.

Many of our projects will have continuous integration (CI) checks that run on a pull request. To ensure your changes will pass, you can often test these locally.

If the project has a `package.json` file, check for the following entries in the `scripts` property:

- `build` - Running `pnpm run build` will confirm that a project successfully compiles. This is common in our TypeScript projects.
- `lint` - Running `pnpm run lint` will ensure that the code style is correct.
- `start` - Running `pnpm start` will confirm that the project boots up successfully.
- `test` - Running `pnpm test` will ensure that the unit and functional tests all pass.

You can also check the `.github/workflows` directory for `.yml` files. These files will describe the actual CI checks that run on your pull request.

Ensuring these checks pass **before** submitting a pull request will streamline our review process.

## Submitting a Pull Request

Once you have all of your changes made and committed, you can push them to your forked repository! Use `git push -u origin <branchname>`, where:

- `-u` tells `git` to set the upstream (see below)
- `origin` tells `git` to push to your fork
- `branchname` tells `git` to push to a branch - this MUST match the name of the branch you created locally.

> [!NOTE]
> By setting the upstream, any subsequent `push` commands can be done with `git push`, and it will be pushed to the same branch.

Now you can open the pull request! You should see a quick option to do so appear at the top of your repository on GitHub. Click the "Pull Request" button to have GitHub automatically set up the pull request.

First, change the title of the pull request to match your branch name (following the conventions above!). Then, follow the instructions in the preset Pull Request template (make sure to complete any steps listed!).

Congratulations! You've submitted your first pull request! We will review it as quickly as possible, so keep an eye out for approvals (or requested changes).

## Pull Request Reviews

All pull requests require a review before being merged. Most reviews will come from Naomi, but some projects may have additional staff who can submit reviews.

If your pull request is approved, it will be merged and deployed depending on the project's deployment schedule and pipeline.

If your pull request requires additional changes or information, we ask that you apply the changes promptly. Contributions with outstanding change requests that receive no activity within a week will be closed as stale.

## Other Contributions

If you aren't comfortable with the codebase, or would like to contribute in other ways, we have options for that!

- Documentation Updates: You are always welcome to update our documentation (like this file!) if you see any typos or anything that can be clarified.
- Feature Requests: If you have ideas for new features or improvements, feel free to open an issue!
- Bug Reports: We rely on our users to help identify bugs - if you see something wrong, please let us know with an issue!

## Holopin Badges

![Virtual badges featuring Naomi, Becca, and Rosalia](https://cdn.nhcarrigan.com/projects/holopin.png)

Contributors are eligible to receive digital [Holopin](https://www.holopin.io/@naomis-novas) badges for their contributions to our projects. To claim your badge, fill out the template in our [Discord community](https://chat.nhcarrigan.com)!
