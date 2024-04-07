## pass

### Create

```bash
pass init [-p] <gpg-id>
pass git init
pass git remote add origin <your.git:repository>
pass git push -u --all
```

### Store

```bash
# Save a new password and additional information (-m --> multiline) (press
# Ctrl + D on a new line to complete):
pass insert [-m] fsf.org/rsc

# Generate a new random password with a given length, and copy it to the
# clipboard (-n --> no symbols):
pass generate [-n] fsf.org/rsc length
```

### Retrieve

```bash
pass ls fsf.org/
pass show fsf.org/rsc
pass -c fsf.org/rsc
```

### Search

```bash
pass find fsf.org
```

### Management

```bash
pass mv fsf.org fsf.org/rsc
pass rm [-rf] fsf.org
pass cp fsf.org/rsc fsf.org/ricosc
```

```bash
pass edit fsf.org/rsc
```

### Synchronize

```bash
pass git push
pass git pull
```

### References

https://passwordstore.org
https://git.zx2c4.com/password-store/about/

---

[[/index|Get Back To Index]]
