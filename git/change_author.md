```
git config --global user.name "New Author Name"
git config --global user.email "<email@address.example>"
```
```
git rebase -r <some commit before all of your bad commits> \
    --exec 'git commit --amend --no-edit --reset-author'
```

