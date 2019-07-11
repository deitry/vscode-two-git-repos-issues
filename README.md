# Steps to reproduce two-repos-in-one-folder issues.

0. Rename `project/.git1` `project-dev/.git1` to `project/.git` and `project-dev/.git` because `git` is not able to add `.git` to staged changes.
1. Open `project` folder in Code and open SCM view. You should see `1` file is untracked.
2. Open file `2` from `project_dev` folder. On SCM sideview nothing is changed.
3. Open `.git_dev/config file` and remove line with `worktree=../`. At the source control view
new provider called project-dev should appear with file `2` as untracked.
4. Put line with `worktree` back. File `1` should appear in `project-dev` instead of `1`

## First issue:
Try to click on `1` at `project-dev` section. An error occures:
```
Unable to open '1': Unable to read file (Error: File not found (/home/user/workspace/two-repos/project-dev/1)).
```
Expected: `/home/user/workspace/two-repos/project/1` is opened.

## Second issue:
Try to reload VS Code and go to Source Control sideview.
Note: files `1` and `2` should be opened in editors.

Expected: `project` and `project-dev` should be listed among Source Control Providers.
Instead only `project` is presented.
If you remove line about `worktree` in `project/.git_dev/config` then `project_dev` would be shown again and you have to add it back if you want to `project-dev` track the right worktree.
