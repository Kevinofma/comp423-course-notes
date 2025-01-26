# How to Use Rust
* Primary author: [Kevin Ma](https://github.com/Kevinofma)

* Reviewer: [Krisha Avula](https://github.com/krisha188)

---
How To Set Up Your Rust Dev Container
---

Step 1: Inital Setup

(A) Open your terminal or command prompt

(B) Create a new directory for your project

``` bash
mkdir rust-project
cd rust-project
```

(C) Initalize a new Git Repository

``` bash
git init
```

!!! note "GitHub Repositories"

    If you would like, you can now create a new repository page on Github so that
    you can link your local repository to Github

(D) Ensure Docker and VS Code are installed before proceeding

Step 2: Setting up the Development Environment

(A) In VS Code, open the rust-project directory via: File > Open Folder

(B) Install the Dev Containers and Docker Extension for VS Code

(C) Create a .devcontainer directory in the root of your project, either through
    the VS Code GUI or with the command mkdir. Create a JSON file inside of this
    new directory called devcontainer.json. The path should be:

  
    .devcontainer/devcontainer.json


(D) The devcontainer.json file defines the configuration for your development environment. Here, we're specifying the following:

* Name: a descriptive name for your dev container

* Image: the Docker image to use, in this case, the latest version of a Rust environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!

* Customizations: adds useful configurations to VS Code, Here we are using the rust-analyzer VSCode plugin by the Rust Programming Language Group

* PostCreateCommand: a command to run after the container is created. In our case, we will be running cargo new project --bin --vcs none

!!! info "Understanding the Post Create Command"

    Similar to GCC and the C programming language, Cargo is rust's program manager and build system. The new command tells Cargo to create a new project directory with whatever name you decide to put after the new command and will initalize a directory with your project name, an src directory, and a starter main.rs rust file. By default, the Cargo new command will automatically create a library project and a git repository on your behalf. To make a executable binary project, we use the --bin flag and since we already made a git repository earlier, we can turn this off using the --vcs none flag.

Step 3: Reopen the Project in a VSCode Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running rustc --version to see your dev container is running a recent version of rust without much effort! (As of this writing: rustc 1.83.0 should be the current version as of Janurary 26, 2025)

Congratulations! You have created your first rust dev container.