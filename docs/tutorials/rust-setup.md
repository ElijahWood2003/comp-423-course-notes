> # "Hello, World" Tutorial for Rust
> * Primary author: [Elijah Wood](https://github.com/ElijahWood2003)
> * Reviewer: [Carmine Anderson - Falconi](https://github.com/carmine-anderson)

Welcome! In this tutorial you will learn how to setup a development container for Rust and code "Hello, world". Rust is a coding language that has burst onto the CS scene in popularity because of its safety, performance, and productivity. Learning the basics through this tutorial will help you grow as a programmer!


## What You Will Learn
+ Create a new local git repository
+ Create a basic Rust dev container in VS Code
+ Understand how the dev container helps us
+ Create a basic program in Rust


## Prerequisites
Make sure you have the following before beginning:

1. A [Github](https://github.com) account
2. [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed
3. Visual Studio Code [(VS Code)](https://code.visualstudio.com/)
4. [Docker](https://www.docker.com/products/docker-desktop) installed
5. Command-line basics


## Part 1: Creating Your Repository
### Step 1: Creating a Local Repository
1. Open a new terminal or command window.
2. Create a new directory (folder) for this project:
```
mkdir basic-rust-program
cd basic-rust-program
```
3. Initialize a new git repository in this directory:
```
git init
```
!!! question "What is ```git init```?"

    git init creates a new invisible repository in our current directy ".git" which will store your future version history to maintain version control.
4. Create a README.md file:
```
echo "Tutorial Link: https://elijahwood2003.github.io/comp423-course-notes/tutorials/rust-setup/" > README.md
git add README.md
git commit -m "Initial commit with README"
```
### Step 2: Create a Remote Repository on Github
1. Log in to your Github and locate [Create New Repository](https://github.com/new).
2. Fill in the details as follows:
#####
- **Repository Name**: basic-rust-program
- **Description**: Basic Rust program based on the tutorial in README.md
- **Visibility**: Public
3. Click **Create Repository**.

### Step 3: Link Your Local Repository to Github
1. Paste the following into your local VS Code terminal:
```
git remote add origin https://github.com/<your-username>/basic-rust-program.git
```
Make sure to replace ```<your-username>``` with your Github username.
2. Type ```git branch``` in the terminal and ensure it says your default branch is ```main```. If it isn't, rename it with ```git branch -M main```.
!!! question "Why do we run this command?"

    In some systems the default branch name is ```default``` - for the sake of keeping the branch names consistent for future commands, it makes it easier to ensure the default branch name is ```main```. 
3. Push your local changes to the Github repository:
```
git push -u origin main
```
4. In your web browser, refresh the Github page and you should see your changes in the Github repository.

## Part 2: Setting Up Your Development Container
### Introduction to Dev Containers
When you are working on a project, you want to ensure you not only have the packages required, but the correct versions of each of those packages to maintain stability of your project. A development container ensures your program works consistently across machines.

### Setup Within VS Code
1. Open up VS Code - click on "Open Folder" then open the ```basic-rust-program ``` directory.
2. Navigate to the extensions tab on the left of your VS Code window. Search "Dev Containers" and download the extension.
3. In the root directory of your project, add a ```.devcontainer``` directory. Then add the following file to this directory: ```.devcontainer/devcontainer.json```.
Within ```devcontainer.json``` paste the following code:
```
{
  "name": "Basic Rust Program",
  "image": "mcr.microsoft.com/vscode/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  }
}
``` 
######
+ ```name```: The title of your dev container.
+ ```image```: The Rust dev container image you will use; in this case, the latest development environment for Rust from Microsoft.
+ ```customizations```: Adds configurations we need for the Rust dev container in VS Code. ```rust-lang.rust-analyzer``` is the extension we need for VS Code to run Rust.

#
???+ warning "WARNING"
    Make sure your docker is opened before you move onto the next step.

    If this next step still doesn't work, make sure you check spelling.

### Reopen Your Project in the Dev Container
Now that you've added the ```devcontainer.json``` file, you're ready to reopen your project in your dev container! To do this press ```Ctrl+Shift+P``` on Windows, or ```Cmd+Shift+P``` on Mac. Then type in "Dev Containers: Reopen in Container," and select the option prompted.

Once your dev container finishes loading, close the current terminal and open a new terminal (Terminal > New Terminal). Ensure you are running the latest version of Rust by typing the command ```rustc --version```. It should be approximately 1.83.0.


## Part 3: Creating a Basic Rust Program
### Creating Your Program
+ Go to a new local terminal in VS Code and run the commands: 
```
cargo new --vcs none basic-program
cd basic-program
```
######
+ ```cargo new --vcs none basic-program```: Creates a new binary project, and the ```--vcs none``` flag removes the automatic function of creating a new .git repository on your behalf. The binary project is composed of a new directory named ```basic-program``` with ```src``` in it and a new ```main.rs``` file within the ```src``` directory. It also includes a ```Cargo.toml``` file which manages the version of your binary project.
+ ```cd basic-program```: Sets our current working directory into this new repository we've created.
!!! question "What is the ```.rs``` file extension?"

    ```.rs``` is the default Rust file extension. Anytime you are writing a Rust program it is important to add this to the end of the file to ensure the program knows it is writing to Rust.

Locate ```main.rs``` and replace the code in it with the following:
```
// Prints "Hello, COMP423!" to the terminal
fn main(){
    println!("Hello COMP423!");
}
```

### Understanding Your Program
- ```//``` indicates a comment to the code; the compiler will ignore everything on the line after it
- ```fn main()``` defines a new function called main for the program to call.
- ```println!``` prints the string within the parentheses to the terminal.

### Compiling and Running
#### There are two options for compiling and running:
- Run ```cargo build```: Compiles your rust code into a new executable. It performs a similar function that ```gcc [file]``` ran in COMP211 for our C programs. Then find the executable file in your directory and type the name of the executable into your terminal to run it.
- Run ```cargo run```: Compiles your code into an executable AND runs it. Doing this is most common to see your results faster and easier

### Stage and Commit Your Changes to Git
Once you're satisfied with your code, run the following in your local VS Code terminal:
```
git add .
git commit -m "Added Hello COMP423 Program"
```

You must then push your edits using the following command:
```
git push origin
```
!!! note "Understanding Git Commands"

    ```git add .``` adds all directory files to the git stage. Essentially, it 'prepares' your changes to be committed. ```git commit -m "First commit"``` commits these staged changes to your version control, storing a snapshop of these files to your version control.




## Citations
- [423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/)
- [Microsoft Dev Containers](https://hub.docker.com/r/microsoft/vscode-devcontainers)