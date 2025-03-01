## Python

### python3.9

You can install Python packages with

```sh
pip3.9 install <package>
```

They will install into the site-package directory `/usr/local/lib/python3.9/site-packages`

### virtual env

#### links

1. https://wiki.archlinux.org/title/Python/Virtual_environment

#### venv

Note: This method replaces the pyvenv script, which is removed in python 3.8.

This tool is provided by python (3.3+):

```sh
python -m venv envname
```

#### activation

Use one of the provided shell scripts to activate and deactivate the environment. This example assumes bash is used.

```sh
source envname/bin/activate
(envname) $
```

Once inside the virtual environment, modules can be installed with pip and scripts can be run as normal.

To exit the virtual environment, run the function provided by bin/activate:

```sh
(envname) $ deactivate
```

---

[[/index|Get Back To Index]]
