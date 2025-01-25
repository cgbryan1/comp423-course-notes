# Setting up a Dev Container for Go

* Primary author: [Caroline Bryan](https://github.com/cgbryan1)
* Reviewer: [Lizzie Coats](https://github.com/escoats)

## Prerequisites
Before attempting to set up your workspace, make sure you’ve completed the following:

1. Create a Github account - link
2. Install git - link
3. Install Docker - link
4. Install VSCode - link

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

