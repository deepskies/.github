# Contributor Guidelines

## How to contribute

1. Read through our `Discussions Page` to start a new conversation and share your
ideas or follow up an existing conversation on a particular feature.

2. Following the discussions, when you have a good idea of the specifics 
of the feature you wish to contribute, open an `Issue` describing the feature. 

3. Then follow the `Contributor Guidelines` on the rest of this page to open
a `Pull Request`_ to contribute the code implementing the new feature.

## GitHub Workflow

### Fork and Clone the A DeepSkies Repository

**You should only need to do this step once**

First *fork* the repository. A fork is your own remote copy of the repository on GitHub. To create a fork:

  1. Go to the repo you want to work on, (we refer to it as `<repo>` in this document)
  2. Click the **Fork** button (in the top-right-hand corner)
  3. Choose where to create the fork, typically your personal GitHub account

Next *clone* your fork. Cloning creates a local copy of the repository on your computer to work with. To clone your fork:

```
   git clone https://github.com/<your-account>/<repo>.git
```

Finally add the `deepskies` repository as a *remote*. This will allow you to fetch changes made to the codebase. To add the `deepskies` remote:

```

  cd <repo>
  git remote add deepskies https://github.com/deepskies/<repo>.git
  
```

### Create a branch for your new feature

Create a *branch* off the `deepskies` main branch.
Working on unique branches for each new feature simplifies the development, review and merge processes by maintining logical separation. 
To create a new branch:


 ```

  git fetch deepskies
  git branch <issue-type>/<issue-description>
  git checkout <your newly made branch>

```
  
 We follow a naming schema that labels the issue as either a `bug` or `feature` depending on what it addresses. 
 If your code addresses a problem you can name it like `bug/broken-thing` or if it's something new to add; `feature/shiny-thing`

### (Optional) Install Pre-Commit 

Many repos include a `.pre-commit-config.yaml`, which helps keep coding conventions standard. 
  We recommend you use them and incorperate them in your own repositories! 
  
  To install the pre-commit: 
  
  ```
  
  pip install pre-commit 
  pre-commit install
  
```
  This now checks your code and modifies it to fit flake8 coding conventions every time you run `git commit`. 
  Note: This will unstage your commit, so you will need to add your code a second time after the pre-commit has cleaned your code. 
  
### (Optional) Set up a virtual enviroment 
  
  Most codebases here use a virtual enviroment, and contain source install instructions. 
  Because you are contributing, using the instructions from the source install will help you get the depedencies you need for each repo. 
  It's better to work within the framework the core team used, so any additional dependencies can be more seemlessly added to the resources, and checked with automatic unit tests. 
  
### Hack away!


Write the new code you would like to contribute and *commit* it to the feature branch on your local repository.
Ideally commit small units of work often with clear and descriptive commit messages describing the changes you made. To commit changes to a file:

```

  git add file_containing_your_contribution
  git commit -m 'Your clear and descriptive commit message'
  
```
  
*Push* the contributions in your feature branch to your remote fork on GitHub:

```

  git push origin <your-branch-name>

```
**Note:** The first time you *push* a feature branch you will probably need to use `--set-upstream origin` to link to your remote fork:

```

  git push --set-upstream origin <your-branch-name>

```
  
### Open a Pull Request


When you feel that work on your new feature is complete, you should create a *Pull Request*. This will propose your work to be merged into the main repository.

  1. Go to the Pull Request page (`https://github.com/deepskies/<repo>/pulls`)
  2. Click the green **New pull request** button
  3. Click **compare across forks**
  4. Confirm that the base fork is `deepskies/<repo>` and the base branch is `development`
  5. Confirm the head fork is `<your-account>/<repo>` and the compare branch is ``<your-branch-name>``
  6. Give your pull request a title and fill out the the template for the description
  7. Reference the issue number that describes the purpose of the code update (using the #) 
  8. Click the green **Create pull request** button

  **Note:** Not every repository has the same base branch, so a reviewer may change the base branch and request changes in case of a merge conflict. 

  
### More Information

More information regarding the usage of GitHub can be found in the [GitHub Guides](https://guides.github.com/).

## Coding Guidelines

### General Guidelines

 All contributions should follow the [PEP8 Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/). 
 We recommend using [`flake8`](https://flake8.pycqa.org/) to check your code for PEP8 compliance.
 Using a pre-commit hook, if included in the repository, will help with this process. 

### Unit Tests

Pull requests will require existing unit tests to pass before they can be merged. 
  Additionally, new unit tests should be written for all new public methods and functions. 
  Unit tests for each submodule are contained in subdirectories called `tests` and you can run them locally using `pytest`. 
	
You can run existing tests using `python3 -m pytest --cov` and verify that your updates have coverage and do not break other tests. 

If your unit tests check the statistical distribution of a random sample, the test outcome itself is a random variable, and the test will fail from time to time, please mark such tests with the `@pytest.mark.flaky` decorator, so that they will be automatically tried again on failure. 
  To prevent non-random test failures from being run multiple times, please isolate random statistical tests and deterministic tests in their own test cases.

### Docstrings

All public classes, methods and functions require docstrings.
They must include: 
  
  - Description
  - Parameters
  - Notes
  - References

We recommend using [VSCode's autodocstrings](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring)
  
 
 _These guidelines were adopted from [SkyPy's](https://github.com/skypyproject/skypy/) Contributor Guidelines. 
  If you like our projects, you'd probably like them too!_
