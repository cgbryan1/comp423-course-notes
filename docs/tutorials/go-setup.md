# Setting up a Dev Container for Go

* Primary author: [Caroline Bryan](https://github.com/cgbryan1)
* Reviewer: [Lizzie Coats](https://github.com/escoats)

## Prerequisites
Before attempting to set up your workspace, make sure you’ve completed the following:

* Create a Github account - link
* Install git - link
* Install Docker - link
* Install VSCode - link

## Setting up Your Local and Remote Repositories

### Creating your local repository

In your VSCode terminal, type the following commands to create and switch into a directory for your project. 

```
mkdir go-project
cd go-project
```

Next, initialize a new git repository for your project.
```
git init
```

Create a README file for your directory.
```
echo "# My Go Project" > README.md
```

Finally, stage and commit your changes to your new repository!
```
git add .
git commit -m "Adding a README file to my Go project."
```



### Creating your remote repository

Navigate to your Github and create a new repository with the **same name as your local repository**. Add whatever description you’d like!



### Linking your local and remote repositories
With your project still open in VSCode, add your Github repository as the corresponding remote repository:
```
git remote add origin https://github.com/<username>/go-project.git
```

For your first push to your remote, you’ll need to specify the upstream:
```
git push --set-upstream origin main
```

After initially specifying the upstream, you can push to your remote repository with this command:
```
git push origin
```

Woohoo! Your local and remote repositories are now set up and linked!


## Setting up Your Dev Container

Step 0: say a prayer to the Docker gods.

### Configure your Dev Container

Open up your "go-project" directory in VSCode again!
1. Navigate to the left sidebar on your screen
2. Click on the extensions tab
3. Download the Dev Containers extension in VSCode

In the root of go-project, create a directory called ```.devcontainer```. Inside of this directory, create a file named ```devcontainer.json```.

The ```devcontainer.json``` file that you just created holds the configuration for your development environment.
Paste this text inside of it:
```
/// put code here eek
```

if you look closely at this code, you can see that we specify the following:
1. name: a name for your dev container
2. image: a base image from microsoft. this tutorial uses one associated with Go.
3. customizations: include extensions needed in your dev container so that they're installed for other developers automatically.
FINISH CUTOMIZE
4. postCreateCommand: the command to run after the container is installed.
FINISH POST

### Configure your Dev Container