# Good research code 
The following practices were adopted from Patrick Mineault's great book [Good Research Code][1]. I've added a few minor details and assume you are interfacing with GitHub through git commands in the Terminal. 

When starting a new project, follow these steps to keep your project organized:  

**1) Import a simple project skeleton.** From the Terminal, go to your local GitHub directory and find your projects folder (may just be the directory labeled 'GitHub', as it is on my computer) and import the CCM Lab's cookiecutter skeleton. For example:

\\$ cd documents/github/projects  
\\$ cookiecutter gh:ccmlab-ubc/project-template

If you've downloaded before and are asked if it's okay to delete and download again, choose 'yes'.   

**2) Follow the directions given in the Terminal following import of the project skeleton.** Specifically, you will want to cd into your new project directory. Next, you will create a virtual environment for your project (give it same name as project) by typing in:  
\\$ conda create --name MY_PROJECT python=3.11  
Then activate the new virtual environment:  
\\$ conda activate MY_PROJECT  
\\$ pip install -e .  

**3) Install commonly used python packages.** 
(Revised on 10/27/23) First install pip with conda:

$ conda install -c anaconda pip

Next, pip install bayes_toolbox as that will give you many of the major pacakges. 

$ pip install bayes_toolbox

You will have to separately install jupyter lab. 

$ conda install -c conda-forge jupyterlab

\\$ conda install pandas numpy matplotlib jupyter scipy  

You can later add the other packages you may need (e.g., jupyterlab). 
  
[**4) In the Terminal, create a .gitignore file.**  
$ nano .gitignore  
Copy the following file types and folders to the list and save:
- .DS_Store
- **/.DS_Store
- **/.egg-info
- **/.ipynb_checkpoints
- data] **Step 4 is not necessary if you've imported the lab's project template (cookiecutter) because the .gitignore file already has these file types in there.**

**5) Create a new repository with the same name (i.e., MY_PROJECT) in your GitHub account.** Copy the SSH_address. 

**6) Initialize your project and sync to GitHub.** From within the project directory, type the following into the command line:
1. git init
2. git add .
3. git commit -m "Initial commit"
4. git branch -M main
5. git remote add origin <SSH_address>
6. git push -u origin main

&nbsp;   
#### **Extras:** ####
**7) Add your virtual environment in Jupyter notebooks.** In the Terminal, make sure you are in the project's virtual environment.   
\\$ pip install --user ipykernel  
\\$ python -m ipykernel install --user --name=MY_PROJECT    
Now each time you create a new notebook, choose the MY_PROJECT kernel from the Kernel dropdown. This will ensure you are only importing packages that are already in your environment, thus making replication across computers a breeze.   

**8) Export environment.yml file.** For exact duplication of your virtual environment, type:  
\\$ conda env export > environment.yml  

**Note:** If you are trying to create an environment using a .yml file that was created on a different operating system, you may run into problems (see: [here][2] and [here][3]). Try to create a new .yml using the following command:  
$ conda env export --no-builds -f environment.yml  

**9) Recreate your virtual environment.** Type the following line into the Terminal:   
$ conda env create --name actual_name_of_environment --file=environment.yml

And [here][4] is another helpful resource on sharing environments. 

&nbsp;  
**Some helpful terminal commands:**  
- conda info --envs (list all virtual environments)
- conda activate envname (to switch to envname)
- conda env remove -n envname (to remove virtual environment envname) 
- jupyter kernelspec uninstall envname (to remove your virtual environment from list of kernels)  


  


  [1]: https://goodresearch.dev/
  [2]: https://goodresearch.dev/setup.html#export-your-environment
  [3]: https://github.com/conda/conda/issues/9399
  [4]: https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/04-sharing-environments/index.html