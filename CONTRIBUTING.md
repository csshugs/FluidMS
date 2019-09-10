# CONTRIBUTING

This document provides a collection of rules and guidelines that need to be adhered to when working with or contributing to FluidMS.

## Commit guidelines

Every commit ever made must adhere to these guidelines.

### Commit title

Each commit message consists of a commit title and an (optional) commit body. Especially for the commit title, we have strict formatting guidelines to follow.

#### Category

The first part of **every** commit title is the category:

* `[FEATURE]` when new code is added for a new feature or a feature is enhanced with additional functionality.
* `[BUGFIX]` when code is added or changed in order to fix a bug.
* `[ADJUST]` when code is altered upon the recommendation of a reviewer or peer developer.
* `[REFACTOR]` when a large part of the code base is rewritten.
* `[BUILD]` when code regarding the build workflow is added or changed.
* `[TESTING]` when code or documentation is added or changed that concerns everything related to testing.
* `[DOCS]` when new documentation is added or existing documentation is changed.

**Formatting:**

* In square brackets
* Upper case

#### Scope

The category is followed by the scope. The scope is the component or feature that the work is done for.

**Example:**

```text
[FEATURE] Page-head:
```

**Formatting:**

* Title case
* Multiple words are hyphenated (then in lowercase)
* The scope ends with a colon

#### Title

What follows after the colon is the actual commit title. It’s meant to describe briefly what changed in this specific commit. The commit title (the entire line) should not exceed 80 characters.

**Example:**

```text
[FEATURE] Page-head: Add new background-color
```

**Formatting:**

* Title case after the colon
* The title has **no** trailing period
* The commit title is written in imperative form

#### Examples

**Bad example:**

```text
[feature] hero banner:added CSS class.
```

* The `[CATEGORY]` is not written in upper case
* The scope is not written in title case
* The scope has a wrong space between the two words
* No space after the colon
* The title does not start in title case
* No imperative form
* Wrong trailing period

**Good example:**

```text
[FEATURE] Hero-banner: Add CSS class for reversed hero-banner title
```

### Commit Body

If 80 characters are not enough to describe your code changes, the changes you made are probably too complex. This is where a proper commit body proves to be a good tool to describe your work in more detail.

What a detailed commit body is **not** intended for is depicting which code in which files has been changed. This information is already in the commit itself automatically. Also documenting what the code itself does in the commit body does not belong there — this should be documented in the form of comments in the code itself.

Rather try to indicate what **was** the case before you made the change, **why** you made a change and what the case is **now**.

It’s critical to leave an **empty line between the commit title and the commit body.** This also means that you have to write your commit message in a dedicated text editor because it’s not possible to write multi-line text via `$ git commit -m "..."`. To do so, you really don’t have to do anything except omitting the `-m` flag in the `$ git commit` command. So when you just run `$ git commit`, you are thrown into the [vim](http://www.vim.org/) text editor by default ([you can change that ](https://help.github.com/articles/associating-text-editors-with-git/)[to any editor you like](https://stackoverflow.com/questions/30024353/how-to-use-visual-studio-code-as-default-editor-for-git/36644561#36644561)). You can type in your full commit message (title + body) and save the file.
