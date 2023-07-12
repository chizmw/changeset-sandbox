# STEPS TAKEN

## Installing

View the [changesets project on GitHub](https://github.com/changesets/changesets/tree/main)

Install the changeset tool:

```sh
yarn add @changesets/cli && yarn changeset init
git add .changeset/ package.json yarn.lock
git commit -m "add the changeset tool"
```

Tweak the config:

Edit [changeset/config.json](.changeset/config.json) and set:

```json
  "commit": true,
```

Then:

```sh
git commit -m "update changeset tool to auto-commit" .changeset/config.json
```

## Enable The Bot

Visit [changeset-bot](https://github.com/apps/changeset-bot) and "_Configure_" as desired:

- some projects
- all projects

## New Branch

So we can see things taking shape, we'll add our first changeset fragments, and
workflows in a branch.

```sh
git checkout -b changesets
```

We will automate based on
[this document](https://github.com/changesets/changesets/blob/main/docs/automating-changesets.md).

We create `.github/workflows/changeset-release.yml` based on
[Example Workflow Without Publishing](https://github.com/changesets/action#without-publishing).

We add it to git:

```sh
git add .github/workflows/changeset-release.yml
git commit -m "add Changeset Release workflow"
```

Before we create our first changeset, we need to fix `package.json`:

```sh
yarn init
git commit -m "update package configuration" package.json
```

To make our first change entry, we'll run `yarn changeset`. We run it once with each of these messages:

- `add changesets tool to project`
- `add changeset release github workflow to project`

![command output from 'yarn changeset'](docs/images/001-yarn-changeset.png)

We confirm that these have been automatically added to git:

```sh
❯ git log --no-decorate --oneline -n2
efe3383 docs(changeset): add changeset release github workflow to project
99af77f docs(changeset): add changesets tool to project
```

We then check things out by pushing our new branch:

```sh
git push -u origin changesets:changesets
```

We then [follow the link](https://github.com/chizmw/changeset-sandbox/pull/new/changesets) to create a new PR.

Shortly after creating the
[PR](https://github.com/chizmw/changeset-sandbox/pull/1),
we see a comment from the bot:

![changeset-bot PR comment](docs/images/002-changeset-bot-pr-comment.png)

To under
