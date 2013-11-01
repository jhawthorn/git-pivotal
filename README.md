
## Demo

http://showterm.io/c87a5df3ed8799444aef1#fast

## Requirements

* ruby 1.9.3+
* pivotal-tracker gem
* git

## Installation

1. `gem i pivotal-tracker`
2. Copy `bin/git-pivotal` and `bin/git-start` somewhere in your PATH.
3. Copy `hooks/prepare-commit-msg` into your repositories hooks directory, `.git/hooks`.

## Configuation

1. Set your API token in your `~/.gitconfig`

        git config --global pivotal.api-token YOUR_API_TOKEN

2. Set your project id in your repository

        git config pivotal.project-id PROJECT_ID

## Usage

git-pivotal is based around assigning an story id to a branch. This is managed
by the git config setting `branch.<NAME>.pivotal-story-id`.

### git pivotal


```
usage: git pivotal ls     # list available stories
   or: git pivotal list   # list available stories (full format)
   or: git pivotal show   # show the current story
   or: git pivotal [start|restart|finish|deliver]
```

`git-pivotal` supports listing and changing states of pivotal tracker stories
based on the current branch.

### hooks/prepare-commit-msg

This belongs in your repository's hooks directory, `.git/hooks`. It fills in
your commit message with the story id for the current branch.

### git start

git-start is a small script which shows one option for using git-pivotal in
your workflow. If you work differently, it's easy to replace.

```
usage: git start STORY_ID NEW_BRANCH
```

`git start` creates a new branch and sets its pivotal tracker story id. 

### Aliases

In addition to the `git start` command, you may want aliases to make using
git-pivotal more natural. The following is from my `~/.gitconfig`

```
[alias]
         i = pivotal ls
         story = pivotal show
         stories = pivotal list
         restart = pivotal restart
         finish = pivotal finish
         deliver = pivotal deliver
```

