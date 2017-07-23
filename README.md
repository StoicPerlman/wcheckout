# wgit
Used in place of git checkout to easily save your working tree on git checkout.

`wgit` stands for "working git" and is a play on the `wget` command name


## Overview
`SRC_BRANCH` = branch before the command was run

`DEST_BRANCH` = branch you want to checkout

When fired, creates a tmp branch `working/SRC_BRANCH`, and commits all working tree changes, before checking out `DEST_BRANCH`.

If `working/DEST_BRANCH` exists, it merges those changes back into `DEST_BRANCH` and resets HEAD back 1 commit to reapply the changes to the working tree.

## Purpose
This is easily done with stash, but I find when jumping around from branch to branch it can get cluttered and I have to search to find the stash I want to reapply.

## Future
Ideally it could run using pre-checkout and post-checkout hooks, however there is no pre-checkout hook.

Overriding the default `checkout` command would also work, but allas you cannot alias default git commands.
