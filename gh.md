## gh

GitHub command-line tool

### links

1. https://formulae.brew.sh/formula/gh#default
2. https://archlinux.org/packages/community/x86_64/github-cli/
3. https://cli.github.com/
4. https://github.com/cli/cli

### commands

#### create a new repository on the command line

```sh
cd ~/your-repo
echo "# your-repo" >> README.md
git init
git add README.md
git commit -m "initial commit"
git branch -M master
git remote add origin git@github.com:your-acc/your-repo.git
git push -u origin master
```

#### push an existing repository from the command line

```sh
git remote add origin git@github.com:your-acc/your-repo.git
git branch -M master
git push -u origin master
```

---

[[/index|Get Back To Index]]
