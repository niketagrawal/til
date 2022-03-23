To fetch all remote branches of a github repository and switch to a particular branch, for example, develop branch, do `git fetch --all` followed by `git switch <some-branch>`

Fork can be updated directly from Github using the fetch upstream button added recently. 

### Rebase vs Merge

Reference: https://www.atlassian.com/git/tutorials/merging-vs-rebasing 

There are two options to update your feature branch with the latest commits in its parent branch: merge the parent branch with the feature branch or rebase the feature branch on top of the new changes in the parent branch

Merging pros
- Preserves the entire commit history

Merging cons
- pollutes the commit history of the feature branch as the new commits in the parent branch are at the tip of the feature branch. Thus, the feature branch will not have one continuous linear block of commits made by the developer for a particular feature. 

Rebasing pros
- The commits in the feature branch are moved at the tip of the new changes in the parent branch. This preserves the linear history of the commits in the feature branch.

Rebasing cons
- The commit hashes of the commits in the feature branch are modified. If the feature branch is shared publicly with other developers, this would lead to the collaboartors seing a completey new set of commits on their side. DO NOT use rebase if the feature branch is being shared publicy, which includes the case when the feature branch is under review in form of a pull request and you wish to make some more changes. In that case, do not rebase the feature branch locally and then update the pull request.

### Merge methods

References: https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github

- A non fast forward merge of a feature branch into the main branch preserves the commits in the feature branch, they are merged to main with a merge commit. This also leads to a non-linear commit history but reviewers can see the commits belong to which feature branch.
- A fast forward merge will happen if the the main branch is the direct ancestor of the feature branch, i.e., the tip of the main branch is the start point of the feature branch. This will not create a merge commit upon the merge of the feature branch into main, the HEAD pointer of main will simply move to the latest commit in the feature branch. The commit history will be linear but the lack of a merge commit will not give any information about which feature does the change belong to. It would seem as if these commits were made on master directly.  


### Detached HEAD

If you wish to go back to a particular commit in time in a code, checking out the code in a branch is preferable because you can look at the children commits as well.
If you only check out the commit by using `git checkout <commit hash>` you end up in a detached HEAD state which meansthat that the HEAD is now pointing to a commit and not to a branch (usually the case). This is still fine if you wish to only look around the code, but if you wish to make new commits it won't be possible to track them. (Ref: Code refinery)
