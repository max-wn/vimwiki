## gh

GitHub command-line tool

### links
https://formulae.brew.sh/formula/gh#default
https://archlinux.org/packages/community/x86_64/github-cli/
https://cli.github.com/
https://github.com/cli/cli

### commands

#### create a new repository on the command line
```bash
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
```bash
git remote add origin git@github.com:your-acc/your-repo.git
git branch -M master
git push -u origin master
```

---

[[/index|Get Back To Index]]
