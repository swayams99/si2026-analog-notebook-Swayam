# Lab Notebook

Maintain Lab notebook here.

# Lab 1: Getting Started with Vi, Linux Commands, and Git

This first lab introduced the basics of working in a Linux terminal, editing files with **vi**, and using Git to create and clone repositories. The main goal was to become comfortable with common command-line tasks, simple text editing, and basic version control. Git is used to track file changes and manage project history, while `git clone` creates a local copy of a remote repository [web:11][web:12].

## Objectives

- Learn basic Linux commands.
- Understand the fundamentals of the `vi` editor.
- Create and clone a GitHub repository.
- Practice adding, committing, and pushing files with Git.

## Linux commands

Linux commands are used to work with files and folders directly from the terminal. Some of the most common commands in this lab are:

```bash
pwd
ls
cd
mkdir
touch
cat
cp
mv
rm
```

- `pwd` shows the current directory.
- `ls` lists files and folders.
- `cd` changes the current directory.
- `mkdir` creates a new folder.
- `touch` creates an empty file.
- `cat` displays file contents.
- `cp` copies files.
- `mv` moves or renames files.
- `rm` deletes files.

These commands form the basic workflow for navigating and managing files in Linux.

## Using vi

The `vi` editor is a terminal-based text editor. It is commonly opened from the command line using `vi filename`. `vi` starts in command mode, and you press `i` to enter insert mode so you can type text [web:16]. Press `Esc` to return to command mode, then use commands like `:w` to save, `:q` to quit, and `:wq` to save and quit [web:16].

### Common vi commands

- `vi filename` opens or creates a file.
- `i` enters insert mode.
- `Esc` returns to command mode.
- `:w` saves the file.
- `:q` quits `vi`.
- `:wq` saves and quits.
- `:q!` quits without saving.
- `x` deletes one character.
- `dd` deletes a line.

## Git and repository setup

Git is used to track changes in a project and maintain version history [web:12]. To start a new project, you can create a repository on GitHub by clicking **New repository**, giving it a name, optionally adding a README, and then creating it [web:12]. After that, you can clone the repository to your local computer using `git clone` [web:11][web:15].

### Creating a repository on GitHub

1. Sign in to GitHub.
2. Click **New repository**.
3. Enter a repository name.
4. Add a description if needed.
5. Choose public or private visibility.
6. Add a README if you want an initial file.
7. Click **Create repository** [web:12].

### Cloning a repository

To download the repository to your computer, open the terminal, move to the folder where you want the project, and run:

```bash
git clone https://github.com/swayams99/si2026-analog-notebook-Swayam.git
```

GitHub explains that `git clone` copies the repository from GitHub to your local machine [web:11][web:15]. After cloning, you can enter the folder and start working on the files.

```bash
cd si2026-analog-notebook-Swayam
```

## Basic Git workflow

A simple Git workflow for this lab looks like this:

```bash
git status
git add .
git commit -m "Add lab 1 notes"
git push
```

- `git status` checks the current state of the repository.
- `git add .` stages all changes.
- `git commit -m` saves a snapshot with a message.
- `git push` uploads the commit to GitHub.

If you are creating a brand-new repository locally, you can first initialize it with `git init`, then add files, commit them, and push them to GitHub.

## Example workflow

1. Open the terminal.
2. Use Linux commands like `ls` and `cd` to move to the desired folder.
3. Clone the repository with `git clone`.
4. Open or create a file using `vi`.
5. Edit the file in insert mode.
6. Save and exit with `:wq`.
7. Use Git commands to stage, commit, and push the changes.

## Conclusion

This lab gave a first introduction to Linux command-line usage, `vi` text editing, and Git repository management. These tools are the foundation for working efficiently in a terminal-based development environment and for keeping project files organized with version control [web:11][web:12][web:16].

