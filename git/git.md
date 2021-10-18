To fetch all remote branches of a github repository and switch to a particular branch, for example, develop branch, do `git fetch --all` followed by `git switch <some-branch>`

Fork can be updated directly from Github using the fetch upstream button added recently. 

### Rebase vs Merge

Reference: https://www.atlassian.com/git/tutorials/merging-vs-rebasing 

There are two options to update your feature branch with the latest commits in its parent branch: merge the parent branch with the feature branch or rebase the feature branch on top of the new changes in the parent branch

Merging pros
- Preserves the entire commit history

Merging cons
- pollutes the commit history of the feature branch as te new commits in the parent branch are at the tip of the feature branch. Thus, the feature branch will not have one continuous linear block of commits made by the developer for a particular feature. 

Rebasing pros
- The commits in the feature branch are moved at the tip of the new changes in the parent branch. This preserves the linear history of the commits in the feature branch.

Rebasing cons
- The commit hashes of the commits in the feature branch are modified. If the feature branch is shared publicly with other developers, this would lead to the collaboartors seing a completey set of commits on their side. DO NOT use rebase if the feature branch is being shared publicy, which includes the case when the feature branch is under review in form of a pull request and you wish to make some more changes. In that case, do not rebase the feature branch locally and then update the pull request.
