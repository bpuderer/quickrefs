Command|Description
---|---
git config --list|list all variables with their values in config file
git config --global user.name "My Name"|set your identity
git config --global user.email user@email.com|set your identity
git help command|git manual for command
git init|create empty git repo
git clone url|creates directory, copies existing repo
git clone url dirname|copies existing repo into specified directory
git status|show working tree status
git add filename|add file (or directory and its contents recursively) to next commit
git add '*.txt'|recursively stage files using wildcard
git add .|stage added, modified, deleted files
.gitignore|file containing patterns of files for git to ignore.  [templates](https://github.com/github/gitignore)
git diff|list unstaged changes
git diff --cached|list staged changes compared to last commit. --staged is a synonym of --cached
git commit|record changes to repo. Text editor launched for commit message
git commit -m 'commit message'|commit with message inline
git commit -m 'concise description ~50 chars' -m 'detailed description'|commit message guideline from Pro Git book
git rm filename|remove file from tracked files as well as working directory (if it exists)
git rm '*.log'|recursively remove using wildcard
git rm --cached filename|unstage and remove from tracked files but keep in working directory
git mv oldname newname|shortcut to rename a file for next commit
git log|view commit history
git log --stat -5|last 5 commits with abbreviated stats
git commit --amend|re-commit
git reset|unstage all files
git reset HEAD filename|unstage file
git checkout -- filename|discard changes to (unstaged) file in working directory
git checkout .|revert changes made to working copy
git remote -v|list url and shortname of remotes
git remote add shortname url|add new remote explicitly
git remote show remotename|info on remote
git remote rename from to|rename remote name
git fetch shortname|downloads updates from remote but does not merge
git pull|fetch and merge into the current branch
git push remotename branch|push changes to remote
git tag|list tags
git tag tagname|create lightweight tag
git tag -a tagname -m 'message'|create annotated tag
git show tagname|display tag info
git tag -a tagname checksum|tag a commit later. Only partial checksum is necessary
git push origin tagname|transfer tag to remote server. git push does not transfer tags to remote servers
git checkout -b branchname tagname|checkout version that looks like a specific tag
git tag -d tagname|delete local tag
git push --delete origin tagname|delete remote tag
git config --global alias.co checkout|create alias
git branch branchname|create branch
git checkout branchname|switch working tree to specified branch
git checkout -b branchname|create branch and switch to it
git merge branchname|merge specified branch into current branch and record as a commit
git branch -a|list remote and local branches
git branch -d branchname|delete branch
git rebase branchname|rebase current branch with specified branch


[Reference Manual](https://git-scm.com/docs)

[Pro Git 2e](https://git-scm.com/book/en/v2) on [github](https://github.com/progit/progit2)
