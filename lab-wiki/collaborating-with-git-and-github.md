# **Collaborating with Git and GitHub**

----

Real ones remember that a big part of our lab philosophy is to practice open science - we want our research, including code, to be replicable. Furthermore, we do a lot of collaboration where it's important for everyone to be on the same page, which means everything should be easily accessible and understandable. Git is a great way to collaborate smoothly and open up your code to the public!

There's a couple ways to go about using Git. Common ones include using Terminal, or using VSCode. Instructions for both are included below.

----

### **Branch Protection**
We can set requirements for pushes to branches and who can approve pull requests through:
1. In repo settings, enable "Require pull request reviews before merging" and "Require reviews from code owners"
2. Create a new file called `CODEOWNERS` in the .github/ directory
3. Write: `*  @username`

----
### **Adding collaborators**

 1. Once in a repository in GitHub, go to **Settings**. 
 2. Click the sidebar item **Collaborators**. GitHub may ask you to confirm your access by entering your password.
 3. There will be a section called **Manage Access**, under which you can use the **Find a collaborator** search bar to add collaborators and manage the access of existing collaborators.


----

### **Cloning a repository**

Cloning a repo means copying all the up-to-date data associated with it. This gives you a space to work with it on your own device.

#### **In Terminal**

 1. Once in a repository, go to the green button labeled **Code**.
 2. From here, copy the **SSH address**. 
 3. In **Terminal**, navigate to the directory you want to clone the repo into and run `git clone <SSH-address>`. Huzzah, the repo is now cloned! 

#### **In VSCode**

You can follow the instructions above to clone the repo in terminal, and then open the folder in VSCode, or clone the repo within VSCode as described:

 1. Once in a repository, go to the green button labeled **Code**.
 2. From here, copy the **SSH address**. 
 3. Open VSCode. On the Welcome page there will be a link that says **Clone Git Repository**. Click this.
 4. VSCode will give you a field to enter the SSH address. Paste the SSH address and hit Enter.

----

### **Creating a branch**

Creating a branch opens up a copy of the repo that you can work on on your personal device. This is great because it prevents you from making bad changes to the main branch - you can fiddle with thinks until you're confident in your changes, then merge with the main branch.

#### **In Terminal**

 1. After cloning a repo, change directory into the cloned repo.
 2. Run `git checkout -b <branch-name>`. Name the branch whatever you'd like, but keep in mind people will see the name when you merge - ideally it should be informative.
 3. Make whatever changes you want in this branch!

#### **In VSCode**

 1. In the bottom left corner of the window there is a small symbol that matches the Source Control symbol on the left sidebar. Click this.
 2. VSCode will prompt you with a few options, including **Create new branch...** Click this.
 3. VSCode will prompt you to create a branch name. Name the branch whatever you'd like, but keep in mind people will see the name when you merge - ideally it should be informative.
 4. VSCode will ask you to **Publish branch**. Do this.
 5. Make whatever changes you want in this branch!

---

### **Committing changes to a file**

To be extra certain you aren't accidentally making bad changes, there are steps to even making changes to branches.

 1.  To add a change, run `git add -A`

Adding is like getting ready to take a snapshot. Essentially, by adding a change you tell Git to start tracking the changes you've made, and you're able to go back and forth between changes without necessarily saving them.

If adding a change is preparing to take a snapshot, committing is actually taking that snapshot. By committing, you finalize a change (to your branch) and create a checkpoint in your project.

#### **Committing changes in Terminal**

 1. To commit a change, run `git commit -m "commit message here"`. The commit message should be short and sweet - anyone should be able to tell at a quick glance what kind of changes you committed.
 2. To push a change to your branch, run `git push origin <branch-name>`.

#### **Committing changes in VSCode**

 1. If it is not already open, click the **Source Control** sidebar option. This will open a helpful panel called **Changes**, under which you will see a text field for a committ message, a blue button that says **Commit**, and a list of changes that you've made.
 2. Click the **plus sign** on the changes that you want to commit - this will add them to the staged changes, which will be included once you actually commit.
 3. To commit, simply click the blue **Commit** button.
 4. If you want to both commit and push, click the dropdown menue on the **Commit** button, and click **Commit & Push**.

----

### **Pull request**

Pull requests are the medium through which your personal changes can be merged with the main branch. Instead of making the changes directly, requesting a change ensures someone with permissions can look over what changes you want to make before approving. Commiting changes automatically triggers the option to make a pull request.

Once you've made a pull request, someone can look over the changes you've made, and if they decide they're good changes they can merge with the main branch!

#### **In Terminal**

 1. To make the pull request, run `git pull origin main`.

#### **In VSCode**

 1. On the **Graph** sidebar, hover over the commit you want to pull request and there will be an option that says **Open in GitHub**.
 2. Clicking this will take you to the online repository, and there will be a helpful yellow alert telling you that there are changes for which a pull request can be made.
 3. Follow the directions from the alert.

----

### **Merge conflicts?**

Merge conflicts occur when you attempt to merge changes, but there are other discrepancies between the branch to be merged and the main branch. Normally this just happens because the branch isn't up to date, and is no biggie. 

To prevent merge conflicts from occurring, however, be sure to pull from the main branch frequently - this'll make sure your version is updated. 

 1. In a merge conflict GitHub will show you the file the merge conflict is in, and there will be some extra text denoting what that file looks like in each branch.
 2. All you need to do is delete any extraneous text and make sure the file looks exactly how you want it to in the final version.

----

```{admonition} **Our Collaboration Workflow**
Now that you have a gist on how Git works. Follow this workflow when collaborating on any repos within our lab:
1. Run `git clone <SSH-address>` (You only need to run this for the first time once)
2. Run `git pull` to update your local with the remote repo
3. Run `git checkout -b <branch-name>` to create and switch to a new branch (You can name the branch with your name)
4. Start coding in your branch!
5. Save and then run `git add -A`
6. Run `git commit -m "commit message here"`
7. Run `git push origin <branch-name>`
8. Open GitHub and follow the directions for making the pull request (from your branch into main)
9. Now to delete your local branch, run `git switch main` then run `git branch -d <branch-name>`
10. Once you need to make more changes, repeat steps 2-9!
```