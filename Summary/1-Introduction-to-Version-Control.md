# 1. Introduction to Version Control
## 1.1 Before Version Control
```
diff file_name1 file_name2
```
Shows line-by-line differences between two files.

```
diff -u file_name1 file_name2
```
Displays unified differences between two files, showing context lines around changes.

```
patch file_name < diff_file_name
```
Applies changes from a diff file to the specified file.

> Resources for more information:
> 
> There are other interesting patch and diff commands such as patch -p1 and diff -r. For more information on these commands, check out the following resources:
> -   [http://man7.org/linux/man-pages/man1/diff.1.html](http://man7.org/linux/man-pages/man1/diff.1.html)
> -   [http://man7.org/linux/man-pages/man1/patch.1.html](http://man7.org/linux/man-pages/man1/patch.1.html)

## 1.2 Using Git
```
git config --global user.email "me@example.com"
git config --global user.name "My name"
```
Sets the global email address and username for future commits.

```
git config -l
```
Lists all Git configuration settings and their values.

```
git init
```
Initializes a new Git repository in the current directory, creating a `.git` subdirectory. Existing repositories are not affected.

```
git add file_name
```
Stages the `file_name` file, preparing it for the next commit.

```
git status
```
Shows the current state of the working directory and staging area, including changes to be committed and untracked files.

```
git commit
```
Records staged changes to the repository with a commit message, opening an editor for message input.

```
git commit -m 'commit message'
```
Records staged changes to the repository with a specified commit message, without opening an editor.

```
git log
```
Displays a list of recent commits, showing commit hashes, authors, dates, and messages.

> Guidelines for writing commit messages:
> 
> A commit message is generally broken into two sections: a short summary and a description of the changes. When the git commit command is run, Git will open a text editor to write your commit message. A good commit message includes the following:
> 
> - **Summary:** The first line contains the summary, formatted as a header, containing 50 characters or less.
> 
> - **Description:** The description is usually kept under 72 characters and provides detailed information about the change. It can include references to bugs or issues that will be fixed with the change. It also can include links to more information when relevant.
>
> Click the link to review an example of a commit message: [https://commit.style/](https://commit.style/)

## 1.3 Glossary Terms
**Commit:** A command to make edits to multiple files and treat that collection of edits as a single change

**Commit files:** A stage where the changes made to files are safely stored in a snapshot in the Git directory

**Commit message:** A summary and description with contextual information on the parts of the code or configuration of the commit change

**Diff:** A command to find the differences between two files

**DNS zone file:** A configuration file that specifies the mappings between IP addresses and host names in your network

**Git:** A free open source version control system available for installation on Unix based platforms, Windows and macOS

**Git directory:** A database for a Git project that stores the changes and the change history

**Git log:** A log that displays commit messages

**Git staging area:** A file maintained by Git that contains all the information about what files and changes are going to go into the next commit

**Modified files:** A stage where changes have been made to a file, but the have not been stored or committed

**Patch:** A command that can detect that there were changes made to the file and will do its best to apply the changes

**Repository:** An organization system of files that contain separate software projects

**Source Control Management (SCM):** A tool similar to VCS to store source code

**Stage files:** A stage where the changes to files are ready to be committed

**Tracked:** A file’s changes are recorded

**Untracked:** A file’s changes are not recorded

**Version control systems (VCS):** A tool to safely test code before releasing it, allow multiple people collaborate on the same coding projects together, and stores the history of that code and configuration
