## Git Ops Basic

### Fork and add upstream

1. Fork a repo and clone to local

2. configuration

	```
	git config --global user.name  **
	git config --global user.mail  **
	```

4. Config remote for the fork

	```
	git remote -v
	git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
	git remote -v
	```

5. Sync the fork

	```
	git fetch upstream master
	git checkout master
	git rebase -i upstream/master
	```

### Multiple commit change

If you use gitlab, it has MR which can include serveral commits, and sometimes,
you may want to change one commit in this MR. Follow the following steps:

1. check the commit id which need to rebase

	```
	git log
	```

2. use the commit id which was older(one before)

	```
	git rebase -i <commit-id>

	```

3. actions can be vary depend on your needs

	- for edit code:
		edit that commit dialog with the one pick --> edit and save

	- for change git message:
	  	change pick --> reword and save

4. change your code and commit

	```
	git add <something>
	git commit --amend
	```

5. rebase finally

	```
	git rebase --continue
	```

### Reference

- https://help.github.com/articles/syncing-a-fork/
- https://help.github.com/articles/configuring-a-remote-for-a-fork/
- Useful Notes about pull request http://www.soimort.org/posts/149/