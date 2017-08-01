# Sho's 15-min Python Env Tutorial

Virtual environments in Python are really handy. They allow you to have dedicated workspace by project. Each workspace can run its own version of python and the project dependencies.

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

Check you actually have Virtualenv

```bash
$ virtualenv --version
```

Create your virtualenv environment

```bash
$ cd your_project_folder
$ virtualenv -p python3 .envname
```

This creates a folder .envname containing all the libraries you need to run your virtual environment. In the example above I specified python3. 

It also includes a version of pip for package installs

---

To activate your new virtual environment

```bash
$ source .envname/bin/activate
(.envname)$
```
From there you can then install your specific project dependencies with requirements.txt file. 

The requirements.txt file is sort of like a manifest of the packages you are installing.

You want to use requirements.txt file as a best practice to track your dependencies and as a directive for pip to install those packages.

If you already have packages installed using pip and you need to add requirements.txt file, you can 'freeze' the environment. This lists the already installed packages to requirements.txt.

To do this simply run this command:

```bash
$ pip freeze > requirements.txt
```

---

Using a command like below will ensure that the packages are only installed in your newly created virtual environment. 

If you deactivate and reactivate that env your dependendices are still in place.

```bash
(.envname)$ pip install -r requirements.txt
```

Deactivating a virtual enviroment is also easy. From within your virtual environment type the below command

```bash
(.envname)$ deactivate
```

---

# Running Python in venv

If you have python3 then you get venv for free. It is very similar to virtualenv, though you probably should not expect to use this with python 2.

Create your virtualenv environment

```bash
$ cd your_project_folder
$ python3 -m venv .envname
```

Similar to virtualenv, this creates a folder .envname containing all the libraries you need to run your virtual environment. In the example above I specified python3. 

---

To activate your new virtual environment

```bash
$ source .envname/bin/activate
(.envname)$
```

In windows this looks like this

```bash
.envname\Scripts\activate.bat
```

---

# Running Python in conda

Anaconda is a very powerful data platform. It has so many tools in its ecosystem to do data analytics. Conda is one of those.

Conda plays the role of package and environment manager. Its syntax is slightly different from the other virtual environment managers. 

Note:It is very tricky to get Anaconda or Conda playing nicely with other such package or environment managers.

My recommendation? If you choose to go with Conda, stick with it all the way. The instructions below assume you have Anaconda or Conda installed.

Create your virtual environment

```bash
$ cd your_project_folder
$ conda create --name .envname python=3
```

The beautiful thing about conda is that it manages all your virtual environments centrally. So, unlike the other environment managers you don't see a local folder in your workspace. It also makes it easy to activate any environment regardless of where you are on your workstation. 

In the example above I specified python3. 

---

To see a list of all your virtual environments, simply run the command below

```bash
conda env list
```

To verify the environment you are in, simply run the command below

```bash
conda info --envs
```


---

To activate your new virtual environment

```bash
$ source activate .envname
(.envname)$
```

In windows this looks like this

```bash
$ activate .envname
```

Deactivating a virtual enviroment is also easy. From within your virtual environment type the below command

In Linux and OS X

```bash
$ source deactivate
(.envname)$
```

In windows this looks like this

```bash
$ deactivate
```
---

Package install using a 'pip install -r requirements.txt equivalent'

Conda provides a way to install packages from a file list. If your packages are already listed in a requirements.txt file, simply run

```bash
$ conda install --yes --file requirements.txt
```
However, if one package fails to install all other dependencies will fail

If creating a new environment and using a requirements file
```bash
$ conda create -n new .envname --file requirements.txt
```

To 'freeze' or create a requirements.txt from a existing environment
```bash
$ conda list -e > requirements.txt
```
---

# Done!

You now have the ability to use python virtual environments in your arsenal

Congratulations!!!
