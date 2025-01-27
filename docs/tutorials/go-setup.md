# Setting up a Dev Container for Go

* Primary author: [Caroline Bryan](https://github.com/cgbryan1)
* Reviewer: [Lizzie Coats](https://github.com/escoats)

* Adapted from [MKDocs tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/) with info from [Go Documentation](https://go.dev/doc/)

## Prerequisites
Before attempting to set up your workspace, make sure you’ve completed the following:

* [Create a Github account](https://github.com/)
* [Install git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
* [Install Docker](https://www.docker.com/get-started/)
* [Install VSCode](https://code.visualstudio.com/download)

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

???+ Note

    The` >` symbol writes the output of the `echo` command to a file called README.md.

Finally, stage and commit your changes to your new repository!
```
git add .
git commit -m "Adding a README file to my Go project."
```



### Creating your remote repository

Navigate to your Github and create a new repository with the **same name as your local repository**. Add whatever description you’d like!

???+ Note

    Make sure your GitHub repository does not initialize a README file;  we already created one locally in the previous step, so there's no need to do it again.

### Linking your local and remote repositories
With your project still open in VSCode, add your Github repository as the corresponding remote repository:
```
git remote add origin https://github.com/<username>/go-project.git
```

For your first push to your remote, you’ll need to specify the upstream:
```
git push --set-upstream origin main
```

???+ note

    The --set-upstream flag creates a tracking relationship between the main branch in your local repository and the one in your remote repository. This flag can be shortened to -u.

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

???+ note

    You should see "Dev Containers" come up as an extension automatically, but if not, its identifier is `ms-vscode-remote.remote-containers`.


In the root of go-project, create a directory called ```.devcontainer```. Inside of this directory, create a file named ```devcontainer.json```.

The ```devcontainer.json``` file that you just created holds the configuration for your development environment.
Paste this text inside of it:
```
{
  "name": "COMP423 Go Tutorial",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  },
  "postCreateCommand": "go mod init comp423-go-tutorial"
}
```

if you look closely at this code, you can see that we specify the following:

1. ```name```: a name for your dev container
2. ```image```: a base image from microsoft. this tutorial uses one associated with Go.
3. ```customizations```: here, we install VSCode's Go plugin.
4. ```postCreateCommand```: the command to run after the container is installed. In our case, this command initializes a go.mod file with comp423-go-tutorial as its path.

### Reopen Project in Dev Container

* Open your command palette in VS Code (Cmd+Shift+P)
* Select **Dev Containers: Reopen in Container**
* Let the container build & start! This might take a minute.

### Verify Your Go Installation

Now that your container is open and running, open up a new terminal and run this subcommand:
```
go version
```
This should output a number - this is the version of Go that you're using!

???+ note

    If you get an error message or don't see a number, double check that you've completed the dev container setup steps correctly.

Congrats, your dev container is all set up and ready!

## Writing + Running Your First Go Program

### Step 1: Write Your Program

Create a new file called ```hello423.go``` in your project's root directory.

Paste in the following code:

```
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")
}
```

**Breaking down this code:**

```package main```: declares a main package, aka a way to group functions. This includes all the files in the same directory.

```import "fmt"```: importing a standard Go library package. This specifically allows you to print text to the console, which we do in the next function!

```func main()```: our main function automatically executes when you run a program in Go. This will print out "Hello COMP423!" to your console, but feel free to replace the text inside the parenthesis with any message you want!

### Step 2: Build and Run Your Program

Before we get started, let's understand the difference between the ```build``` and ```run``` commands in Go.

```go run```: this command will compile and run your program *temporarily*. It requires a Go environment to execute, and does not create an executable object file!

```go build```: this command compiles your program and creates a single, static binary executable object file. Since this file is statically linked, it contains all dependencies. You don't need a Go environment to run this file!

**a side note about gcc:**

```gcc```: Just like `go build`, this command allows us to compile our program into an executable object file. While `gcc` offers us more flexibility in linking and compiling, it also is more complex and requires more effort. Since we want to quickly compile *and* execute our programs, we'll stick with the above go subcommands in this tutorial!

Now that we understand our go subcommands, we can run our program!

#### Run Your Program Locally + Temporarily:

Copy this code into the terminal of your VSCode project:

```
go run main.go
```

This will run the main function of your go program! You should see the following output:

```
Hello COMP423!
```

#### Fully Build + Run Your Program:

To build an executable object file of your program, run the following in your project's VSCode terminal:

```
go build -o hello_comp423 main.go
```

This will return an executable object file named ```hello_comp423```. Feel free to change the name in the command above!

To run this compiled file, use the following code (adjusting the file name if necessary):

```
./hello_comp423
```

## Closing Notes

You did it! At this point, you've set up your own Dev Container with a functioning Go environment, written your first Go program, and learned how to run and export it! 🎉🎉🎉🎉

If you enjoyed this Go tutorial, my venmo is @carolinebryann. I also accept poems as tokens of appreciation. 🤭