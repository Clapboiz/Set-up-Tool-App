# Undo a commit & redo
git reset --hard HEAD~

# Revert to a Previous Commit

| Command             | Function                                                                                     | Advantages                                                                                                                                                                               | Disadvantages                                                                                                                  |
|---------------------|----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| `git reset`         | Moves HEAD to a specific commit, can remove uncommitted changes depending on the mode.     | - Allows reverting changes and going back to the state of the project at a specific commit. - Flexible with soft, mixed, and hard modes.                                                  | - May lead to unintended loss of changes if not careful.                                                                       |
| `git revert`        | Creates a new commit to revert changes from a specific commit, does not delete the original commit. | - Safer as it does not alter the commit history of the project. - Preserves the commit history of the project, making it easy to track the reverted changes.                           | - Creates a new commit, increasing the number of commits in the project history. - Not suitable when wanting to completely delete changes of a commit. |
| `git reset --soft <commit_id>`   | Moves HEAD to a specific commit, keeps changes in the index and working directory.          | - Preserves changes so you can continue editing and commit without having to re-add them.                                                                                               | - Requires manual steps to commit changes again after using this command.                                                        |
| `git reset --mixed <commit_id>`  | Moves HEAD to a specific commit, keeps changes in the working directory but not in the index. | - Allows previewing changes before adding them to the index for committing. - Does not remove changes from the working directory.                                                         | - Requires adding changes to the index and committing manually after using this command.                                       |
| `git reset --hard <commit_id>`   | Moves HEAD to a specific commit, removes all uncommitted changes in the index and working directory. | - Reverts to the state of the project at a specific commit without keeping any changes.                                                                                                  | - Loss of uncommitted changes that cannot be recovered after using this command.                                                 |

# Untrack the files from Git
If you have a file named `access.log` and `error.log` and when you have a `.gitignore` file and it still pushes to github, this means that the cache of these two files has not been removed.

Now you just need to follow what I suggest

Navigate to the root directory of your project and use the git rm --cached command to untrack these files.

```
git rm --cached <yourFile or yourFolder>
git rm --cached <yourFile or yourFolder>
```

```
git commit -m "Remove log files from being tracked"
```

```
git push origin <branch-name>
```
