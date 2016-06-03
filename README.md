# Introduction
 This script is implemented according to the [pete-otaqui's bumpversion.sh](https://gist.github.com/pete-otaqui/4188238 )
 and Vincent Driessen's [A Successful Git Branching model](http://nvie.com/posts/a-successful-git-branching-model/)
# Usage
  1. copy this two script into your project and in master branch
    ```bash
    ./bumpversion # add VERSION and CHANGES to project
    ```
  2. when in dev
    ```bash
    ./bumpversion # will not exec script
    ./release     # will think that you want to create a new `release` branch
                  # [0.1.0] -> [0.2.0] or [0.1.11] -> [0.2.0] or type any version you want
                  # default: increment(minor, 1), patch = 0
    ```
  3. when in release-major.minor.patch
    ```bash
    ./bumpverion  # exec when all work done, test fine, and ready to be merged to master and dev
    git push      # push the CHANGES and VERSION file

    git checkout master
    git merge --no-ff release-major.minor.patch
    ./bumpversion # it will tag version
    git push --tags

    git checkout dev
    git merge --no-ff release-major.minor.patch
    git branch -d release-major.minor.patch # now you can delete the branch
    ```
  4. when in hotfix-major.minor.patch
    ```
    ./bumpversion # exec when all work done, test fine, and ready to be merged to master and dev
                  # version changed
                  # [0.1.0] -> [0.1.1], [0.11.8] -> [0.11.9]
                  # default: patch++
                  # and the rest is something like above. Think you get it!
    ```
