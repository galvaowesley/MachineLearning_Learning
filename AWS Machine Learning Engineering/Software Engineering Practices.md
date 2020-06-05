###### tags: `AWS Machine Learning Engineer`

Software Engineering Practices 
===

# Clean and Modular Code


- **PRODUCTION** CODE: software running on production servers to handle live users and data of the intended audience. Note this is different from production quality code, which describes code that meets expectations in reliability, efficiency, etc., for production. Ideally, all code in production meets these expectations, but this is not always the case.
- **CLEAN**: readable, simple, and concise. A characteristic of production quality code that is crucial for collaboration and maintainability in software development.
- **MODULAR**: logically broken up into functions and modules. Also an important characteristic of production quality code that makes your code more organized, efficient, and reusable.
- **MODULE**: a file. Modules allow code to be reused by encapsulating them into files that can be imported into other files.

# Refactoring Code

* **REFACTORING**: restructuring your code to improve its internal structure, without changing its external functionality. This gives you a chance to clean and modularize your program after you've got it working.
* Since it isn't easy to write your best code while you're still trying to just get it working, allocating time to do this is essential to producing high quality code. Despite the initial time and effort required, this really pays off by speeding up your development time in the long run.
* You become a much stronger programmer when you're constantly looking to improve your code. The more you refactor, the easier it will be to structure and write good code the first time.

# Writing Clean Code

**Meaningful Names**

Tip: Use meaningful names: 

* Be descriptive and imply type
* Be consistent but clearly differentiate
* Avoid abbreviations and especially single letters
* Long names != descriptive names 

**Nice Whitespace**


Tip: Use whitespace properly

* Organize your code with consistent indentation - the standard is to use 4 spaces for each indent. You can make this a default in your text editor.
* Separate sections with blank lines to keep your code well organized and readable.
* Try to limit your lines to around 79 characters, which is the guideline given in the PEP 8 style guide. In many good text editors, there is a setting to display a subtle line that indicates where the 79 character limit is.

[PEP 8 guidelines for code layout](https://www.python.org/dev/peps/pep-0008/?#code-lay-out)

# Efficient Code

Optimizing code to be more efficient can mean making it:

* Execute faster
* Take up less space in memory/storage

# Documentation 


* DOCUMENTATION: additional text or illustrated information that comes with or is embedded in the code of software.
* Helpful for clarifying complex parts of code, making your code easier to navigate, and quickly conveying how and why different components of your program are used.
* Several types of documentation can be added at different levels of your program:
    * **In-line Comments - line level:** They are used to explain parts of your code, and really help future contributors understand your work.
   ```python
  # any comment here
  any code here
   ```
    * **Docstrings - module and function level** Docstring, or documentation strings, are valuable pieces of documentation that explain the functionality of any function or module in your code. Ideally, each of your functions should always have a docstring. 
        [Docstring Conventions](https://www.python.org/dev/peps/pep-0257/) 
    ```python
    def population_density(population, land_area):
    """Calculate the population density of an area."""
    return population / land_area
    ```
    
    * **Project Documentation - project level**

# Version Control

## Scenario #1

Let's walk through the git commands that go along with each step in the scenario you just observed in the video above.
STEP 1: You have a local version of this repository on your laptop, and to get the latest stable version, you pull from the develop branch.

> Switch to the develop branch
> 
> `git checkout develop`



> Pull latest changes in the develop branch
> 
> `git pull`

STEP 2: When you start working on this demographic feature, you create a new branch for this called demographic, and start working on your code in this branch.

>    Create and switch to new branch called demographic from develop branch
> 
>    `git checkout -b demographic`
> 
>    Work on this new feature and commit as you go
> 
>    `git commit -m 'added gender recommendations'`
>   `git commit -m 'added location specific recommendations'`
    

STEP 3: However, in the middle of your work, you need to work on another feature. So you commit your changes on this demographic branch, and switch back to the develop branch.

>   Commit changes before switching
>
>   `git commit -m 'refactored demographic gender and location recommendations '`
>
>   Switch to the develop branch
>
>   `git checkout develop`

STEP 4: From this stable develop branch, you create another branch for a new feature called friend_groups.

    Create and switch to new branch called friend_groups from develop branch

    git checkout -b friend_groups

STEP 5: After you finish your work on the friend_groups branch, you commit your changes, switch back to the development branch, merge it back to the develop branch, and push this to the remote repository’s develop branch.

>    Commit changes before switching
> 
>   `git commit -m 'finalized friend_groups recommendations '`
> 
>    Switch to the develop branch
> 
>   `git checkout develop`
> 
>    Merge friend_groups branch to develop
> 
>    `git merge --no-ff friends_groups`
> 
>    Push to remote repository
> 
>    `git push origin develop`

STEP 6: Now, you can switch back to the demographic branch to continue your progress on that feature.

>    Switch to the demographic branch
> 
>    `git checkout demographic`

## Scenario #2

Let's walk through the git commands that go along with each step in the scenario you just observed in the video above.
Step 1: You check your commit history, seeing messages of the changes you made and how well it performed.

>    View log history
> 
>    `git log`

Step 2: The model at this commit seemed to score the highest, so you decide to take a look.

>    Checkout a commit
> 
>    `git checkout bc90f2cbc9dc4e802b46e7a153aa106dc9a88560`

After inspecting your code, you realize what modifications made this perform well, and use those for your model.
Step 3: Now, you’re pretty confident merging this back into the development branch, and pushing the updated recommendation engine.

>    Switch to develop branch
> 
>    `git checkout develop`
> 
>    Merge friend_groups branch to develop
> 
>    `git merge --no-ff friend_groups`
> 
>    Push changes to remote repository
> 
>   `git push origin develop`

## Scenario #3

Let's walk through the git commands that go along with each step in the scenario you just observed in the video above.
Step 1: Andrew commits his changes to the documentation branch, switches to the development branch, and pulls down the latest changes from the cloud on this development branch, including the change I merged previously for the friends group feature.

>    Commit changes on documentation branch
> 
>    `git commit -m "standardized all docstrings in process.py"`
> 
>    Switch to develop branch
> 
>    `git checkout develop`
> 
>    Pull latest changes on develop down
> 
>    `git pull`

Step 2: Then, Andrew merges his documentation branch on the develop branch on his local repository, and then pushes his changes up to update the develop branch on the remote repository.

>    Merge documentation branch to develop
> 
>    `git merge --no-ff documentation`
> 
>    Push changes up to remote repository
> 
>    `git push origin develop`

Step 3: After the team reviewed both of your work, they merge the updates from the development branch to the master branch. Now they push the changes to the master branch on the remote repository. These changes are now in production.

>    Merge develop to master
> 
>    `git merge --no-ff develop`
> 
>    Push changes up to remote repository
> 
>    `git push origin master`

For the most part, git makes merging changes between branches really simple. However, there are some cases where git will be confused on how to combine two changes, and asks you for help. This is called a merge conflict.

Mostly commonly, this happens when two branches modify the same file.

For example, in this situation, let’s say I deleted a line that Andrew modified on his branch. Git wouldn’t know whether to delete the line or modify it. Here, you need to tell git which change to take, and some tools even allow you to edit the change manually. If it isn’t straightforward, you may have to consult with the developer of the other branch to handle a merge conflict.

## Model Versioning


Version control in data science can be tricky, because there are many pieces involved that can be hard to track, such as large amounts of data, model versions, seeds, hyperparameters, etc.

[How to Version Control Your Production Machine Learning Models](https://blog.algorithmia.com/how-to-version-control-your-production-machine-learning-models/)

---

# Testing

Testing your code is essential before deployment. It helps you catch errors and faulty conclusions before they make any major impact. Today, employers are looking for data scientists with the skills to properly prepare their code for an industry setting, which includes testing their code.


* Problems that could occur in data science aren’t always easily detectable; you might have values being encoded incorrectly, features being used inappropriately, unexpected data breaking assumptions
* To catch these errors, you have to check for the quality and accuracy of your analysis in addition to the quality of your code. Proper testing is necessary to avoid unexpected surprises and have confidence in your results.
* TEST DRIVEN DEVELOPMENT: a development process where you write tests for tasks before you even write the code to implement those tasks.
* UNIT TEST: a type of test that covers a “unit” of code, usually a single function, independently from the rest of the program.
