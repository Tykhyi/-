# Work-case 1
## **Discipline:** 
Операційні системи

## Student:
Андрій Тихий РПЗ-33

## What is Git?
Git is a distributed version control system that has become the standard in modern software development. However, its role is much wider than just "saving files" because it is a versatile tool that has four key functions: Version Control, a Communication System between developers, the Foundation of Teamwork, and Data Security.

### **Version Control**
You can compare Version Control to a save system in a computer game. Git takes snapshots of the whole project at specific times. This way, if you make a mistake by accident, Git allows you to go back to any previous working version, just like loading an old save file in a game. Also, Git lets you analyze the history of the code and how the project developed from the first file to its current state.

### **Communication System**
As a Communication System, Git acts as a link for the team through code. When changing code, the team can leave comments (commits) to explain why they made a specific decision. It also keeps a detailed record: who made the changes, when they happened, and, most importantly, what exactly was changed.

### **Foundation of Teamwork**
If it weren't for Git, teamwork would turn into a chaos of sending files back and forth. That is why it is also called the Foundation of Teamwork. This is possible because many developers can work on the same project at the same time. One person can design the interface, another can write database logic, and they will not disturb each other. In the end, they can merge their work into one finished product. Everything is very convenient, organized, and efficient.

### **Data Security**
Finally, Git ensures Data Security because it stores the whole project history locally, creating copies on every team member's disk, not just on one server. So, if the main server breaks or the internet goes down, you won't lose your progress because you have your own complete copy of all the data.

## Main commands

`git config --global user.name "Name"` — sets the username.<br>
`git config --global user.email "email"` — sets the email address.<br>
`git init` — used for a new project. It creates a hidden .git folder, and from this moment, Git starts tracking changes in this folder.<br>
`git clone <URL>` — used to download an existing project (for example, from GitHub) to your computer.<br>
`git status` — the most important command. It shows the current state: which files are changed, which are new, and which are ready to be saved (are in the Staging Area).<br>
`git add <file>` — adds a specific file to the list ready for saving.<br>
`git add .` — adds all modified files at once. This moves changes to the Staging Area.<br>
`git commit -m "Description"` — takes a "snapshot" of the project and saves it to history forever. The -m parameter is mandatory to add a comment and avoid using a complex text editor.<br>
`git log` — shows a list of all saves (who, when, and what they did).<br>
`git branch` — shows a list of all existing branches.<br>
`git branch <name>` — creates a new branch.<br>
`git checkout <name>` — switches you to another branch (allows you to "jump" between versions).<br>
`git checkout -b <name>` — a combined action: creates a branch and switches to it immediately.<br>
`git merge <name>` — combines changes from the specified branch into the one you are currently in.<br>
`git push` — sends your local commits to the server (GitHub).<br>
`git pull` — pulls the latest changes from the server to your computer (this combines the fetch and merge commands).<br>
Pull Request (PR) — this is not a terminal command, but a process on the GitHub website where you propose your changes for review before merging them with the main code.<br>
`.gitignore` — this is a special file where you write the names of files or folders that should not be in the repository (for example, passwords, system files, temporary files).<br>
