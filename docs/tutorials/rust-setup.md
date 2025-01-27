# How to Use Rust :fontawesome-brands-rust:
* Primary author: [Kevin Ma](https://github.com/Kevinofma)

* Reviewer: [Krisha Avula](https://github.com/krisha188)

* Adapted from <https://comp423-25s.github.io/resources/MkDocs/tutorial/#understanding-your-cicd-workflow>

## Intro
Rust is a programming language with a large emphasis on performance and type safety. In this tutorial, we are creating a rust dev container and building and running our first rust program.

## Prerequisites
Before completing this tutorial make sure you have:

1. A GitHub account: Make a github account if you do not already have one

2. Install git: If its not installed, then install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

3. Visual Studio: If its not installed, then install [VS Code](https://code.visualstudio.com)

4. Docker: This is needed to run your dev container. Install [Docker here](https://www.docker.com/products/docker-desktop/)


## How To Set Up Your Rust Dev Container

### Step 1: Inital Setup

1. Open your terminal or command prompt

2. Create a new directory for your project

    ``` bash
    mkdir rust-project
    cd rust-project
    ```

3. Initalize a new Git Repository

    ``` bash
    git init
    ```

4. Ensure Docker and VS Code are installed before proceeding


!!! note "GitHub Repositories"

    If you would like, you can now create a new repository page on Github so that
    you can link your local repository to Github
    
    1.  Log into your github account
    2.  Create a new repository
        * Fill in the details for your repositories name and description as you would like
        * Chose to make the repository private or public
        * Add a README or gitignore file as you would like
    3.  Link your repository
    ``` bash
    git remote add origin https://github.com/username/projectname.git
    ```

### Step 2: Setting up the Development Environment

1. In VS Code, open the rust-project directory via: File > Open Folder

2. Install the Dev Containers and Docker Extension for VS Code

3. Create a .devcontainer directory in the root of your project, either through
    the VS Code GUI or with the command mkdir. Create a JSON file inside of this
    new directory called devcontainer.json. The path should be:

  
    .devcontainer/devcontainer.json


4. The devcontainer.json file defines the configuration for your development environment. Here, we're specifying the following:

    * ``` name ```: a descriptive name for your dev container

    * ```image```: the Docker image to use, in this case, the latest version of a Rust environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!

    * ```customizations```: adds useful configurations to VS Code, Here we are using the rust-analyzer VSCode plugin by the Rust Programming Language Group
    
    ``` JSON
    {
      "name": "Rust Dev Container",
      "image": "mcr.microsoft.com/devcontainers/rust:latest",
      "customizations": {
          "vscode": {
          "settings": {},
          "extensions": ["rust-lang.rust-analyzer"]
        }
      }
    }
    ```

### Step 3: Reopen the Project in a VSCode Dev Container

1. Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

2. Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running rustc --version to see your dev container is running a recent version of rust without much effort!


!!! note "Version"
    Rustc 1.83.0 should be the current version as of Janurary 26, 2025 

Congratulations! You have created your first rust dev container.

Creating a Basic Rust Program

Step 1: Initalizing and Creating Your First Rust Project

1. Open a new terminal in VS Code and run the following command:

    ```bash
    cargo new your-project-name --bin --vcs none
    ```

    !!! info "Cargo"

        Similar to GCC and the C programming language, Cargo is rust's program manager and build system. The new command tells Cargo to create a new project directory with whatever name you decide to put after the new command and will initalize a directory with your project name, an src directory, and a starter main.rs rust file. By default, the Cargo new command will automatically create a library project and a git repository on your behalf. To make a executable binary project, we use the --bin flag and since we already made a git repository earlier, we can turn this off using the --vcs none flag.

2. Navigate to your newly created main.rs file found in ```/your-project-name/src```. Your main.rs file should look like the following

    ```rust
    fn main() {
        println!("Hello, world!");
    }
    ```

    MAKE AN INFO ADMONITION OF THIS:
    Title: Explaning main.rs
    Body:
        1. ```fn```: This keyword declares a function in Rust. It is used to define the beginning of a function declaration.
        2. ```main```: This is the name of the function. In Rust, main is a special function because it's the entry point of any executable program. When you run a Rust program, the main function is the first code that gets executed.
        3. ```()```: These parentheses are part of the function declaration syntax. In this case, main takes no arguments, so the parentheses are empty.
        4. ```{``` and ```}```: These curly braces define the body of the function. Any code within these braces is part of the main function.
        5. ```println!("Hello, world!);```: This is a rust macro. It takes the string "Hello, world!" and prints it to the terminal. The ```!``` denotes that this is a rust macro as opposed to a started rust function call. Macros allow the function to change their behavior and generate code based on the number or type of arguments passed through the function, allowing for function overloading and other usefull tricks. In this case, the rust macro we are using is println. Similar to C or Java, the function call ends with ```;```

    
    If you would like, replace ```"Hello, world!"``` with whatever you wish to print in the terminal, for the purposes of this tutorial, we are changing the string to ```"Hello COMP423"```

Step 2: Building and Running Your Rust Project

1. To run your code, in the terminal, use the command

    ```bash
    cargo build
    ```

    This creates an executable object file located under a new directory under your project in ```/target/debug```.

    CREATE A NOTE ADMONITION with this:
    body: An equivalent to this that you have seen before is running the ```GCC -o your-project-name main.c``` command from COMP 211.

2. You can then run this file using by doing ```./your-project-name```

3. Alternatively, you can build your executable object and run your code in one line using the command:

    ```bash
    cargo run
    ```

    This does the same as running the two commands above all in one line!


Congratulations, you have created your first rust project!


