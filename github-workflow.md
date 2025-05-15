# Collaborating with git and GitHub

Basic steps:
1) Create an empty folder with the project name wherever you keep your GitHub directories/repos
1) Go to GitHub and click on the green **New** button to create a new repo
1) Next, you'll see the setup pages. These are instructions for connecting the repo you just created in GitHub (remote) to the directory you created locally on your computer (local). 
1) Copy the lines after "...or create a new repository on the command line"
1) Paste those lines into terminal while you are cd'ed in the directory you just created locally.
1) You'll see a bunch of stuff happen in the terminal after you hit return and now your local and remote are connected.
1) At the start of each session, remember to always pull from the main branch of origin (i.e., the repo you created on GitHub).
1) When you want to work on stuff, create a new branch first. ```git checkout -b <name of new branch>```
1) Maker sure the new branch name is informative. 
1) Work on the file. Make some changes. Remember to add and commit often. 
1) When you've accomplished the task you set out to complete, you can push your branch to the remote. ```git push origin <name of new branch>
1) This will trigger a pull request. 
1) Assign one pull request reviewer for each repo. This should be the person in charge of the main branch. 
1) The reviewer will review your changes. Look over changes by clicking on "Commits" tab. 
1) If satisfied, reviewer will merge your branch with the main. 

Questions and basic functionality:
- How to clone?
    - ```git clone <https>```
- Why ```git add```? Think of adding as getting ready to take a snapshot. ```git commit``` is actually taking the snapshot. This is useful in cases where you are working on multiple files, and maybe you're ready to take a snapshot of one file but any others. You can then just add that one file, while continuing to make changes to the other files. 
- Reverting commits.
- Reverting adds. 
- Branching. 
- Using cookiecutter: Should you first install project-template or create repo and then install?
    - fix cookiecutter's .gitignore (there's multiples; maybe only use the one in the root?)
    
- git: diff, restore (restore previous version of file / get rid of uncommitted changes), revert (undo a commit), log

Fun facts:
- You can push a new branch to the remote. After creating a new branch, push the branch up with ```git push origin <new-branch-name>. The above will turn into a pull request to merge into the main. Remember: you don't have to merge. 

