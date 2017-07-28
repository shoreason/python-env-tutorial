# Sho's 15-min Python Env Tutorial

Virtual environments in Python are really handy. They allow you to have dedicated workspace by project. Each workspace can run its own version of python and the projective dependencies.

In this model you don't have to worry about conflicts in library version for each project. You essentially provide an isolated working environment.

This tutorial will assume you have python and pip already installed. I'll try to call out a nuances to specific python versions though most of this should carry over.

The 3 approaches to cover include:
- virtualenv
- venv
- conda

---

# Running Python in virtualenv

Install Virtualenv

```bash
$ pip install virtualenv
```

Create your virtualenv environment

```bash
$ cd your_project_folder
$ virtualenv -p python3 .envname
```

This creates a folder .envname containing all the libraries you need to run your virtual environment. In the example above I specified python3. It also includes a version of pip for package installs

--

To activate your new virtual environment

```bash
$ source .envname/bin/activate
(.envname)$
```
From there you can then install your specific project dependencies with requirements.txt file. That file is sort of like a manifest of the packages you are installing.

You want to use requirements.txt file as a best practice to track your dependencies and as a directive for pip to install those packages.

--

Using a command like below will ensure that the packages are only installed in your newly created virtual environment. If you deactivate and reactivate that env your dependendices are still in place.

```bash
(.envname)$ pip install -r requirements.txt
```

Deactivating a virtual enviroment is also easy. From within your virtual environment type the below command

```bash
(.envname)$ deactivate
```

---

