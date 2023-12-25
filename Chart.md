# How I Git-Flow
Make sure you are familiar with the following concepts:
* Git (branching, merging, pushing)
* Git-Flow

## Branches

* Production (always deployable): ````master````
* Development (containing features for the **next** release): ````develop````
* Feature for development: ````feature/xxx````
## Prefixes

* Hotfixes for production: ````hotfix/````
* Features for development: ````feature/````

#### Prefix Examples

* A fix for a bug in production that's causing users' data to inadvertently be deleted:

  ````
  hotfix/DEV-123-stop-accidentally-deleting-users-data
  ````

* A new feature, to allow users to request a password reset

  ````
  feature/DEV-456-user-password-reset
  ````

## I do it all from the command line.

### Features

#### Start a new feature

    # Checkout develop branch, and make sure it's up to date
    git checkout master
    git pull origin master
    
    # Create my new branch
    git checkout -b feature/DEV-123-my-new-feature
    
    # Get things done
    ... write some code ...
    ... write some tests ...

#### Finish a feature
 
    # Create PR feature/DEV-123-my-new-feature onto *develop* and await reviewer
    Create PR from feature/DEV-123-my-new-feature onto develop

    # fix conflict
    git checkout feature/DEV-123-my-new-feature
    git merge --no-ff develop
    git push origin feature/DEV-123-my-new-feature

    # Delete finished branch locally and remotely
    git branch -d feature/DEV-123-my-new-feature
    git push origin :feature/DEV-123-my-new-feature
    
### Hotfixes

#### Start a hotfix
    # Checkout master branch, and make sure it's up to date
    git checkout master
    git pull origin master
    
    # Create my new branch
    git checkout -b hotfix/DEV-456-stop-catching-on-fire
    
    # Get things done
    ... write some code ...
    ... write some tests ...

#### Finish a hotfix
    # Merge my hotfix onto develop and push
    git checkout develop
    git merge --no-ff hotfix/DEV-456-stop-catching-on-fire
    git push origin develop
    
    # Create PR my hotfix onto *master* 
    Create PR from hotfix/DEV-456-stop-catching-on-fire into master
    
    # Delete finished branch locally and remotely
    git branch -d hotfix/DEV-456-stop-catching-on-fire
    git push origin hotfix/DEV-456-stop-catching-on-fire

#### Relesase
    # merge develop onto master
    Create PR from develop onto master
    # create tag, choose master branch, add release note in remote repository

    ![](/gitflow.jpg)

    
