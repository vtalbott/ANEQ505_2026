---
title: Module 1
draft: false
tags:
  -
---
 
### Introduction to Alpine
#### What is Alpine?
- The CU Boulder High Performance Cluster (HPC)
- Basically, it is a supercomputer that is located at CU Boulder and CSU has access to

#### System Architecture
When you are trying to visualize what a supercomputer looks like, you can picture something like this:

![[Pasted image 20260119152224.png]]
#### Alpine Hardware:
- AMD Milan compute nodes
    - 64 cores / node
    - ~240 GB ram / node
    - An average laptop has around 4 cores & 8-16 GB ram, so each node is about 16X more powerful than your average laptop
- High memory AMD Milan compute nodes 
    - 48 cores / node
    - ~1 TB ram / node (😱)  
- - GPU nodes
- Special high compute storage 
- Omni-path network
    - If we had an omni-path network, we could interconnect and put all of our laptops together to do one job to make a supercomputer
    - Alpine's resources combined with its omni-path network makes it a supercomputer
- General parallel file system (GPFS) - distribute and manage data across multiple servers
![[Pasted image 20260120095520.png]]
#### **Nodes**

Alpine has different kinds of nodes. For the purpose of this class, you can think of a node as different computer modes where you are given different types of compute resources and are meant for running different tasks. You can access these nodes in several ways (explained below). Alpine has 4 different types:

- **Login node**
    - This is where you "land" when you login
    - Do not run commands while in login
    - For script editing and job submissions  
          
        
- **Compile node**
    - Translates human-readable source code that we give into computer-executable machine code
    - Used to install software
    - This is where we will install QIIME2
    - Use `acompile` to start a compile session  
          
        
- **Compute node**
    - We do not navigate into these
    - This is where jobs run after submission
    - There are different kinds of compute nodes
    - Here is a list of the compute node resources available on Alpine ([link to more detailed info hereLinks to an external site.](https://curc.readthedocs.io/en/latest/clusters/alpine/alpine-hardware.html "(opens in a new window)") )
    - Use `sbatch` to submit jobs  
          
        
- **Interactive node**
    - We can navigate here to run jobs interactively 
    - We will use an interactive node to run our Qiime2 commands
    - Use `ainteractive` to start an interactive session

**Directories (fancy word for folders)**

There are also different **storage spaces** within Alpine that are meant for different things. 

- **Home directory**
    - /home/$USER
    - This is where you "land" when you first login
    - Not for direct computation
    - Small quota (2 GB)
    - Backed up  
          
        
- **Scratch directory**
    - /scratch/alpine/$USER
    - 10 TB quota - can ask for more if needed
    - High performance storage for computation
    - Files are purged after 90 days of inactivity - **Be careful about this!!!**
    - Folders will persist   
          
        
- **Project directory**
    - /projects/$USER
    - Mid-level quota (250 GB)
    - Large file storage
    - Not high performance storage
    - Backed up - if you choose to use Alpine for long-term storage, this is where you keep your files

Think of these spaces like folders on a computer, where "home" is a folder within "/" (root directory), and "$USER" is a folder within "home", and so on.

![[Pasted image 20260120095618.png]]

--------------------------------------------------------------
### Logging into Alpine

We will use the On Demand website to launch a terminal window that will connect us to the Alpine cluster.

1. Navigate to [ondemand-rmacc.rc.colorado.edu. Links to an external site.](http://ondemand-rmacc.rc.colorado.edu/ "(opens in a new window)")You should see this webpage:
![[Pasted image 20260120095716.png]]

2. Change ORCID to Colorado State University and click Log On.  
      
3. You will next be prompted to login with your NetID.
![[Pasted image 20260120095737.png]]

4. You will then be prompted to use Duo to authenticate.
![[Pasted image 20260120095811.png]]

5.  You should see the CU Research Computing OnDemand landing page.
![[Pasted image 20260120095841.png]]

6. Launch a terminal session by clicking on Clusters at the top and then select >_ Alpine. This should open a new window that looks like this:
![[Pasted image 20260120095909.png]]

You have successfully logged into Alpine!

--------------------------------------------------------------
### File Transfers

When doing your microbiome analyses on Alpine, you will need a way to transfer files from your local computer to Alpine and vice versa. While there are several ways of doing this, our preferred way is to use OnDemand or FileZilla.  

**OnDemand**

1. After logging in, click on Files. You will see paths to your Home, Scratch, and Projects directories. Click on one!
![[Pasted image 20260120100117.png]]

2. This will show you all your folders and files in that directory. 
![[Pasted image 20260120100144.png]]

3. From here you'll be able to:
    - Download files
    - Upload files
    - Rename files
    - Delete files
    - View contents of a file
    - Open a terminal window from that location

--------------------------------------------------------------

### Linux Navigation

Now we will go over general commands to use on the command line. These will work on MacOS and Linux systems, but not necessarily PCs. Here is the "anatomy" of what a basic command might look like.
![[Pasted image 20260120100236.png]]

- First, you have the **command** itself. `ls` is a command that says to list the files in your current working directory, which you can think of as the "folder" you are currently in. 
- You can supply **options** to the command.
    - For example, `ls -a` is saying to list _all_ of the files in your current directory, including any hidden files that start with a ".". 
    - The `-l` option says to list the directory contents in a long listing format
    - The `-G` option says to not print group names in a long listing
    - Explore more options to supply to the ls command [hereLinks to an external site.](https://man7.org/linux/man-pages/man1/ls.1.html "(opens in a new window)")
- You can supply **arguments** to the command.
    - The last line of the graphic above is saying to list all hidden files in a long listing format in the Downloads directory.

These are some common commands that you should learn, as we will use them throughout the semester:
![[Pasted image 20260120100256.png]]