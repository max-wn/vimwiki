## Python

### brew logs
#### python3.9

Python has been installed as
  `/usr/local/bin/python3.9`

Unversioned and major-versioned symlinks `python`, `python3`, `python-config`, `python3-config`, `pip`, `pip3`, etc. pointing to
`python3.9`, `python3.9-config`, `pip3.9` etc., respectively, have been installed into
  `/usr/local/opt/python@3.9/libexec/bin`

You can install Python packages with
  `pip3.9 install <package>`
They will install into the site-package directory
  `/usr/local/lib/python3.9/site-packages`

tkinter is no longer included with this formula, but it is available separately:
  `brew install python-tk@3.9`

If you do not need a specific version of Python, and always want Homebrew's `python3` in your PATH:
  `brew install python3`

### virtual env

#### links
https://wiki.archlinux.org/title/Python/Virtual_environment

#### venv
Note: This method replaces the pyvenv script, which is removed in python 3.8.

This tool is provided by python (3.3+):
```
python -m venv envname
```

#### activation

Use one of the provided shell scripts to activate and deactivate the environment. This example assumes bash is used.
```
source envname/bin/activate
(envname) $
```

Once inside the virtual environment, modules can be installed with pip and scripts can be run as normal.

To exit the virtual environment, run the function provided by bin/activate:
```
(envname) $ deactivate
```



---

[[/index|Get Back To Index]]
