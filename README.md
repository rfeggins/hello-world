# Overview
Sample repository 

## References
a. [Python Installation](http://flask.pocoo.org/docs/1.0/installation/)
b. [Create environment](http://flask.pocoo.org/docs/1.0/installation/#install-create-env)

In this tutorial we will be using the Python 3.4, Flask and setup a virtual 
environment to manage the dependencies.

## Virtual environments
The more Python projects you have, the more likely they will require to use different Python libraries versions, or even Python itself for different projects.  Virtual environments allow teams to set up independent groups of Python libraries that can be used for each project. Packages installed for one project will not affect other projects or the operating system’s packages.

## Creating a Dev environment
Python 3 comes bundled with the **venv** module to create virtual environments. If you’re using a modern version of Python, you can continue on to the next section.

1. To use **venv** you need to create an environment
```
Create a project folder and a venv folder within:

mkdir myproject
cd myproject
python3 -m venv venv
```

2. Activate the environment
Before you work on your project, activate the corresponding environment:
```
. venv/bin/activate
``

3. Install Flask
Within the activated environment, use the following command to install Flask:
```
pip install Flask
```


No - although the environment is 100% there, if someone else where to pull it down the path environment hasn't been exported not to mention Python version discrepancies will likely crop up.

The best thing to do is to create what is known as a requirements.txt file.

When you have created your environment, you can pip install this and pip install that. You'll start to built a number of project specific dependencies.

Once you start to build up a number of project dependencies I would then freeze your local python environment (analogoues to a package.json for node.js package dependency management). I would recommend doing the following in your terminal:

(local_python_environment) $ pip install django && pip freeze > requirements.txt

(local_python_environment) $ pip install requests && pip freeze > requirements.txt
That is to say, freeze your environment to a requirements.txt file every time a new dependency is installed.

Once a collaborator pulls down your project - they can then install a fresh python environment:

$ python3 -m venv local_python_environment
(* Please use Python 3 and not Python 2!)

And then activate that environment and install from your requirements.txt which you have included in your version control:

$ source local_python_environment/bin/activate

(local_python_environment) $ pip install -r requirements.txt
Excluding your virtual environment is probably analogous to ignoring node_modules!
