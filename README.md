# The Data Foundations Labs 

![location of fork button in GitHub](./images/fork_button.png)

Welcome to the first lab of the Data Foundations course. As you can see the lab instructions are in English. 

Python is increasingly becoming the standard programming language for data applications and so we will use python during the labs. Prior knowledge of python is not required but it can help. We will start with a python crash course to get you up to speed. For the lab we use [jupyter notebooks](https://jupyter.org/) which is a popular intuitive tool well suited to experiment and develop python code. 

We will use Github Classroom to distribute the labs. This will also be used to evaluate your work. Make sure to push your work to the repo before the deadline!

To make sure that everyone works in the same environment this lab will be done on a VM in the Azure Cloud. With the [Azure for Students](https://azure.microsoft.com/en-us/free/students/) program you receive $100 Azure credit plus several free services which should be more than sufficient for the course labs. Assuming you stop the VM after working on the lab and you do not spend your credit on other purposes.

Below you can find step-by-step instructions on how to set-up the VM.

# Lab 1: Pandas

Working with data can be challenging: it often doesn’t come in the best format for analysis, and understanding it well enough to extract insights requires both time and the skills to filter, aggregate, reshape, and visualize it. This session will equip you with the knowledge you need to effectively use pandas – a powerful library for data analysis in Python – to make this process easier.

Pandas makes it possible to work with tabular data and perform all parts of the analysis from collection and manipulation through aggregation and visualization. While most of this session focuses on pandas, during our discussion of visualization, we will also introduce at a high level Matplotlib (the library that pandas uses for its visualization features, which when used directly makes it possible to create custom layouts, add annotations, etc.) and Seaborn (another plotting library, which features additional plot types and the ability to visualize long-format data).

The material for this lab is based on a [workshop on Pandas](https://github.com/stefmolin/pandas-workshop) by Stefanie Molin ([@stefmolin](https://github.com/stefmolin)).

## Outline

The labs are divided into the following sections:

### Section 0: Python 101
We start with a crash course on python. A more in depth tutorial can be found [here](https://docs.python.org/3/tutorial/)

### Section 1: Getting Started With Pandas
We will begin by introducing the `Series`, `DataFrame`, and `Index` classes, which are the basic building blocks of the pandas library, and showing how to work with them. By the end of this section, you will be able to create DataFrames and perform operations on them to inspect and filter the data.

### Section 2: Data Wrangling
To prepare our data for analysis, we need to perform data wrangling. In this section, we will learn how to clean and reformat data (e.g., renaming columns and fixing data type mismatches), restructure/reshape it, and enrich it (e.g., discretizing columns, calculating aggregations, and combining data sources).

### Section 3: Data Visualization
The human brain excels at finding patterns in visual representations of the data; so in this section, we will learn how to visualize data using pandas along with the Matplotlib and Seaborn libraries for additional features. We will create a variety of visualizations that will help us better understand our data.

### Section 4: Hands-On Data Analysis Lab
We will practice all that you’ve learned in a hands-on lab. This section features a set of analysis tasks that provide opportunities to apply the material from the previous sections.

---

## Setup Instructions

### Azure for students account
Sign up for your free [Azure for students](https://azure.microsoft.com/en-us/free/students/) account by registering with your school email. You will receive $100 credits)

### VS Code
Download and install [Visual Studio Code](https://code.visualstudio.com/) on your local machine.

### Creating Azure Virtual machine
1. Go to the [Azure portal](https://portal.azure.com/) and click on `+ Create a resource`, find the `Virtual machine` service and click on `Create`. 

![fig1](./images/resource.png)              ![fig2](./images/VM.png)

2. Insert the basic information for your VM:
    - Make sure the subscription is `Azure for Students`
    - Make a new Resource group (for example `Data-Foundations`)
    - Choose a name for the VM (for example 'DF-lab')
    - Set the region to West-Europe
    - Make sure you choose this image: `Ubuntu 18.04 LTS with Python and Docker`
    - Set the size of the VM to `Standard_B2s`
    - Choose SSH for the Authentication type
    
![fig3](./images/VM_basic.png)

3. Go to the `Networking` tab and click `create new` for public IP. Make sure to choose `Basic` SKU and `Dynamic` Assignment.

    ![fig4](./images/IP.png)

4. Under the `Management` tab tick the `Enable auto-shutdown` to avoid large bills
    
    ![fig5](./images/shutdown.png)

5. Go the the `Review + create` tab and click `create`.

6. Download your private key and save it in the `~./ssh` folder.

### Using VS Code to connect to your VM with SSH

1. Go to your VM in the Azure console and copy your public IP (this will be different each time you restart the VM)

    ![fig6](./images/publicIP.png)

2. Open VS Code.

3. Select `Remote-SSH: Connect to Host...` from the Command Palette (F1, Ctrl+Shift+P)

4. Click `+ Add New SSH Host...`

5. type `ssh -i ~/.ssh/DF-lab_key.pem azureuser@20.160.99.1` (where you replace the IP address with the one for your VM from step 1)

6. Choose the `~/.ssh/config` file to save your connection details

7. Click Connect. A new VS Code window will open that is connected to your VM

Next time you connect you will have to choose `Remote-SSH: Connect to Host...` -> `Configure SSH Hosts...` to change the IP address. Then you can just click the name of the connection.

### Cloning the repo to your VM

1. In the Github Classroom repo click on Code and copy the link. 

    ![fig7](./images/repo.png)
    
2. In your VS Code that is conncted to your VM go to `SOURCE CONTROL`, choose `Clone Repository` and paste the Github link.

    ![fig8](./images/clone_repo.png)

### Installing Miniconda on your VM, create a virtual environment and launch Jupyterlab

1. Open a terminal on your VM and go to the `conda` folder and type `bash Miniconda3-py39_4.12.0-Linux-x86_64.sh` and follow the instructions.

2. Go to the main pandas folder and create and activate a virtual environment: 
```shell
(base) azureuser@DF-lab:~$ cd pandas 
(base) azureuser@DF-lab:~/pandas$ conda env create --file environment.yml
(base) azureuser@DF-lab:~/pandas$ conda activate pandas
(pandas) azureuser@DF-lab:~/pandas$
```

3. Launch jupyter lab:
```shell
(pandas) azureuser@DF-lab:~/pandas$ jupyter lab
```

### Keeping costs at a minimum: stop your VM

- Always stop your VM when you are ready by going to the VM resource and clicking the stop button.
    
    ![fig9](./images/stop.png)
    
- Keep a regular eye on your costs in the `Cost analysis` service under the `Cost management`. 

    ![fig10](./images/cost.png)