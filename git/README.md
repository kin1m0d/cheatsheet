# Update an outdated master branch
https://stackoverflow.com/questions/1125968/how-do-i-force-git-pull-to-overwrite-local-files
```
git fetch --all
git reset --hard origin/master
```

# Delete branch
```
git branch -d <local-branch>
```






# Delete pushed commit
https://ncona.com/2011/07/how-to-delete-a-commit-in-git-local-and-remote/#:~:text=To%20remove%20a%20commit%20you,your%20changes%20to%20the%20remote.&text=Notice%20the%20%2B%20sign%20before%20the,git%20to%20force%20the%20push.

- `git rebase -i HEAD~2`
- Remove the commit line, then it is removed locally
- To remove the remote one
- `git push origin +master`
- That didn't work because of some restrictions?
- But as workaround, it is possible to remove the branch in stash, with the commit
	
```
git rebase -i HEAD~2
git push origin +bugfix/LCGCORESPO-2774
```


# Squash commit 
Git: how to squash commits already pushed (https://magonye.github.io/post/git-squash/)
Basically you squash multiple commits into one big commit
TL;DR
1. You use git log while on your working branch and you have pushed everything and from there you find the commit hash of the latest commit before your changes
2. You then do git rebase -i <commit_hash_from_above> and git will guide you through the changes, usually you squash everything into your first commit for the work, then also adjust the commit message for that commit
3. You git push -f to force it to rewrite history on your branch
4. Raise the pull request as expected

Fixup |	keep original message and discard the message from the fixup commit
--- | ---
Squash | Combine the messages of the original and the squash commit


# How to squash commits in git after they have been pushed?
A lot of problems can be avoided by only creating a branch to work on & not working on master:
`git checkout -b mybranch`
The following works for remote commits already pushed & a mixture of remote pushed commits / local only commits:
```
# example merging 4 commits
git checkout mybranch
git rebase -i mybranch~4 mybranch
# at the interactive screen
# choose fixup for commit: 2 / 3 / 4
git push -u origin +mybranch
```
From <https://stackoverflow.com/questions/5667884/how-to-squash-commits-in-git-after-they-have-been-pushed> 


# Cherry pick 
> git cherry-pick <commit hash> as Nikos said should be your friend here since you already pushed your commits to your branch that lives on the remote server.While on the already (pushed) existing branch you created do a git log, this will give you the hash ID for your latest commit (work you did on the branch).You then create another branch out of phase2, checkout that branch and do git cherry-pick <hash id> and git will apply all the changes done to that commit on the old branch, to the new branch. You then commit and push as expected and get rid of the old branch.

> FYI cherry picking sometimes doesn't work if there's a merge between two applied hashes

  
  
# Change last commit message
1. Navigate to the repository.
2. Amend the message of the latest pushed commit:
`git commit --amend -m "New commit message."`
3. Force push to update the history of the remote repository:
`git push --force branch-name`
From <https://linuxize.com/post/change-git-commit-message/> 

  
  
# Add to last commit
https://medium.com/@igor_marques/git-basics-adding-more-changes-to-your-last-commit-1629344cb9a8


`$ (some_branch) git add changelog.md`
- And amend it:
`$ (some_branch) git commit –amend`

- Amending a Commit Without Changing Its Message
- If you don’t want to change your commit message, you can run the amend command with the no-edit flag, like this:
`$ (some_branch) git commit --amend --no-edit`
  
- Pushing an Amended Commit
- If you haven’t pushed the last commit yet to your remote, a single push is enough. Otherwise, you’ll have to push using the -f option since you’ve rewritten your commit history:
`$ (some_branch) git push -f origin some_branch`

- Or simply 
`git push –f`


