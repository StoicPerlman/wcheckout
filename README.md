# wgit
Used in place of git checkout to easily save your working tree on git checkout.

`wgit` stands for "working git" and is a play on the `wget` command name

This comes in two versions. A script and a post-checkout hook. Either will do the job. The post-checkout hook is a bit messy because you have to recheckout the original branch and control when the hook fires within the hook itself. If you are just tring to understand what this does I suggest looking at the script. For actual use, the post-checkout hook is the way to go because it can fire within a git gui.

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
