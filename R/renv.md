[[_TOC_]]

# Introduction

## What is renv?

`renv` is a package management system for R that helps ensure
reproducibility and portability of R projects. It allows you to create
isolated environments for your R projects, making it easier to share and
collaborate on code. The documentation is available at:
<https://rstudio.github.io/renv/articles/renv.html>.

## Why should you use renv?

For different analysis you might rely on various R packages. However,
managing package versions and dependencies can be challenging. Here\'s
why `renv` is a good practice for biologists:

1.  Reproducibility: `renv` allows you to capture the exact versions of
    R packages used in your project. This ensures that your code can be
    reproduced in the future, even if new package versions become
    available.

2.  Collaboration: With `renv`, you can more easily share your R
    projects with colleagues or collaborators. They can set up the same
    environment using the `renv.lock` file, ensuring that everyone is
    working with the same package versions.

3.  Avoid conflicts: By using isolated environments `renv` makes it
    easier to avoid conflicts between different package versions,
    ensuring that your code runs consistently, even if you need to
    update a package for another analysis.

# Implementing renv in your R projects

## Installing renv

To start using `renv`, you need to install it first. Open your R console
and run the following command:

``` python
install.packages("renv")
```

## Working with R projects

Working with R Projects in RStudio is necessary to use `renv`. But it is
a good practice in general as it provides a structured and efficient way
to manage your R scripts, data, and other files. Here are some reasons
why you should always be using R Projects:

1.  Organization: R Projects help you keep all related files in one
    place. This makes it easier to manage your scripts, data, and
    outputs, ensuring that your work is well-organized.

2.  Reproducibility: R Projects ensures that your working directory is
    set correctly every time you open the project. This helps avoid
    issues related to file paths and makes your analysis reproducible.

3.  Collaboration: R Projects make it easier to collaborate with others.
    By sharing the project folder, your collaborators can easily access
    all the necessary files and run the analysis without any issues.

4.  Version Control: R Projects integrate seamlessly with version
    control systems like Git. This allows you to track changes, revert
    to previous versions, and collaborate more effectively with others.

5.  Environment Management: R Projects allow you to manage your R
    environment more effectively. You can use packages like `renv` to
    create isolated environments for each project, ensuring that package
    versions and dependencies are consistent.

**How to Create an R Project, you ask?**

Creating an R Project in RStudio is simple:

1.  Open RStudio.
2.  Go to `File` \> `New Project`.
3.  Choose `New Directory` or `Existing Directory` depending on your
    needs.
4.  Follow the prompts to set up your project.

## Initializing renv in a project

Once `renv` is installed, you can initialize it in your R project. Open
your R console, navigate to your project directory, and run the
following command:

``` python
renv::init()
```

This will modify the `.Rprofile` file, as well as create an `renv/`
directory and a `renv.lock` file in your project, which will be used to
manage your project\'s environment as follows:

-   `renv.lock`: This file captures the exact versions of packages used
    in your project. It ensures that the same package versions are used
    when the project is shared or restored.

-   `renv/` folder: This folder contains the isolated environment for
    your project. It stores the packages and their dependencies specific
    to your project.

## Managing packages with renv

To add packages to your project, you can use the same usual functions,
e.g.:

``` python
install.packages("dplyr") 
BiocManager::install("DESeq2")
```

This will install the package in your project\'s environment only. Once
you have installed the packages that you want, you can update the
`renv.lock` file by running:

``` python
renv::snapshot()
```

You can run this command at any time, for example when you add or update
some packages.

At some point you might use one of the two following commands:

-   the `renv::status()` command compares the current state of the
    project\'s environment with the `renv.lock` file. It identifies any
    changes made to the environment, such as installing or updating
    packages. This helps you track the modifications made to the
    environment and ensures that the project remains reproducible.

-   the `renv::restore()` command restores the project\'s environment to
    the state captured in the `renv.lock` file. It installs the exact
    package versions specified in the file, ensuring that the project
    can be reproduced with the same environment. This is useful when you
    want to recreate the environment on a different system or restore it
    after modifications.

## Sharing your project with renv

To share your project with others, you can share the `renv.lock` file.
Remember to run the `renv::snapshot()` command to capture the current
versions of packages used in your project.

## Recreating a renv environment from a `renv.lock` file 

To recreate the same environment using the `renv.lock` file, you can use
the `renv::restore()` function. Here are the steps to do this:

1.  Navigate to a new or desired R project.

2.  Make sure the `renv.lock` file is located in the R project
    directory.

3.  Execute the following command to restore the environment:

``` python
renv::restore()
```

This command will read the `renv.lock` file and install the exact
versions of the packages specified in the file. It will recreate the
environment as it was when the `renv.lock` file was created.

# Conclusion

Using `renv` in your R projects as a biologist can greatly improve
reproducibility, collaboration, and portability. By managing package
versions and dependencies, you can ensure that your code remains
consistent and can be easily shared and reproduced. Find out more about
`renv` usage by reading their documentation at
<https://rstudio.github.io/renv/articles/renv.html>.

