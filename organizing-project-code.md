# Organizing project code
The following practices were adopted from Patrick Mineault's great book [Good Research Code](https://goodresearch.dev/). I've added a few minor details and assume you are interfacing with GitHub through git commands in the Terminal (see [Resources](resources) page). When starting a new project, follow these steps to keep your project organized:  

## Step 1: Import a simple project template.
From the Terminal, go to your local GitHub directory (it may just be the directory labeled 'GitHub', as it is on my computer) and import the CCM Lab's cookiecutter project skeleton. For example:
```
cd documents/github/projects  
cookiecutter gh:ccmlab-ubc/project-template
```

If you've downloaded this before and are asked if it's okay to delete and download again, choose 'yes'.   

## Step 2: Follow the directions given in the Terminal.
AFter importing the project template, you will want to go to your new project directory. Next, you will create a virtual environment for your project (give it same name as project) by typing in: 

```
conda create --name MY_PROJECT python=3.11
```
 
Then activate the new virtual environment:  
```
conda activate MY_PROJECT  
pip install -e .
``` 

## Step 3: Install commonly used python packages.  
Install pip with conda:

```
conda install -c anaconda pip
```

Next, pip install `bayes_toolbox` as that will give you many of the major pacakges. 

```
pip install bayes_toolbox
```

You will have to separately install Jupyter Lab. 

```
conda install -c conda-forge jupyterlab
conda install pandas numpy matplotlib jupyter scipy  
```
  
You can later add any other packages you may need (e.g., `seaborn`). 


## Step 4: In the Terminal, create a .gitignore file.  

**Note:** Step 4 is not necessary if you've imported the lab's project template (cookiecutter) because the .gitignore file already has these file types in there.**

Otherwise, in the Terminal type:
```
nano .gitignore
``` 

Copy the following file types and folders to the list and save:
- .DS_Store
- **/.DS_Store
- **/.egg-info
- **/.ipynb_checkpoints
- data


## Step 5: Create a new repository with the same name as your project on GitHub.

From the landing page of your GitHub account, click the green "New" button and name it `MY_PROJECT` (or whatever you actually named it). 

Copy the SSH_address. 

## Step 6: Initialize your project and sync to GitHub.

From within the project directory, type the following into the command line:

```
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <SSH_address>
git push -u origin main
```

---
## Extras

### Step 7: Add your virtual environment in Jupyter notebooks.

In the Terminal, make sure you are in the project's virtual environment. 

```
pip install --user ipykernel  
python -m ipykernel install --user --name=MY_PROJECT
```
    
Now each time you create a new notebook, choose the MY_PROJECT kernel from the Kernel dropdown. This will ensure you are only importing packages that are already in your environment, thus making replication across computers a breeze.   

### Step 8: Export environment.yml file.

For exact duplication of your virtual environment, type:  
```
conda env export > environment.yml  
```

**Note:** If you are trying to create an environment using a .yml file that was created on a different operating system, you may run into problems (see: [here](https://goodresearch.dev/setup.html#export-your-environment) and [here](https://github.com/conda/conda/issues/9399)). Try to create a new .yml using the following command: 

```
conda env export --no-builds -f environment.yml  
```

### Step 9: Recreate your virtual environment.

Type the following line into the Terminal:  
```
conda env create --name actual_name_of_environment --file=environment.yml
```

And [here](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/04-sharing-environments/index.html) is another helpful resource on sharing environments. 


### Some helpful terminal commands:

To list all virtual environments:
```
conda info --envs
```

To switch to the environment named `envname`:
```
conda activate envname
```

To remove the virtual environment `envname`:
```
conda env remove -n envname
```

To remove your virtual environment from the list of kernels:
```
jupyter kernelspec uninstall envname 
```
