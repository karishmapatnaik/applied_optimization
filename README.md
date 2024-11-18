# YALMIP with Gurobi Installation Guide (64-bit Windows Machine)
Ths guide will help install YALMIP and Gurobi independently and then point MATLAB to the Gurobi location so that YALMIP can access Gurobi solver.

## Step 1: Install YALMIP
The easiest way to install YALMIP is via tbxManager. So let us first install the tbxManager by going to https://www.tbxmanager.com/ and following the steps. Basically, 
1. Make sure you are running Matlab R2009a or later
2. Create a directory tbxmanager
3. Go to that directory in Matlab
4. Run the following line by line in MATLAB:
```
urlwrite('http://www.tbxmanager.com/tbxmanager.m', 'tbxmanager.m');
tbxmanager
savepath
```
5. Edit/create startup.m in your Matlab startup folder and put the following line there:
`tbxmanager restorepath`
6. Next, install YALMIP by running the following command in MATLAB
```
tbxmanager install yalmip
```
> [!NOTE]
> Every time, you start MATLAB, you need to run this command: `tbxmanager restorepath` to add all the external toolboxes to your MATLAB path, if you do not want to add it to the MATLAB startup script as mentioned in Step 1.5

** YALMIP Installation Complete!

## Step 2: Install Gurobi 
We need to install Gurobi and request a free academic license. 

### Downloading the software
We will download the software first.
1.	Visit the Download Gurobi Optimizer page and download the version you need, as well as the README.txt.
2.	Follow the instructions in README.txt to install the software.
   
### Requesting a free academic license
Next step is to request for a free license key
1.	Navigate to https://www.gurobi.com/features/academic-named-user-license/
2.	Register for a free Gurobi account by using your ASU ID and log in. Please note that you need to be on ASU network to access it. You may use VPN to do that if you are working from a home network. 
3.	Navigate to the licenses tab on the left hand side corner and request a new license. Once you have it, use the download icon on the right hand side corner of the License to download the license key. 

### Linking the software and the license
For Windows: In the start menu, run grbgetkey using the argument provided on the Academic License Detail page (ex: grbgetkey ae36ac20-16e6-acd2-f242-4da6e765fa0a). The grbgetkey program will prompt you to store the license file on your machine. 

>[!NOTE]
>Alternatively, you can also run the Gurobi Interactive Shell by simply typing `gurobi interactive shell` in your Windows start menu. Upon the shell startup, simply copy paste the license key to activate it.

** Gurobi Installation Complete!

## Step 3: Point Gurobi to MATLAB 
Now that YALMIP and Gurobi are independently installed, we need to point YALMIP to find Gurobi by adding it to MATLAB’s path. To begin, you'll need to tell MATLAB where to find the Gurobi routines. The Gurobi MATLAB setup script, gurobi_setup.m, can be found in the <installdir>/matlab directory of your Gurobi installation
+ the default <installdir> for Gurobi 11.0.2 is /opt/gurobi1102/linux64 for Linux
+ the default <installdir> for Gurobi 11.0.2 is c:\gurobi1102\win64 for 64-bit Windows
+ the default <installdir> for Gurobi 11.0.2 is /Library/gurobi1102/macos_universal2 for Mac

To get started, locate the installdir and navigate to the folder in MATLAB, then run the `gurobi_setup.m` file. Alternatively, run the following commands:
```
cd <installdir>/matlab
gurobi_setup
```
** Linking Done!

## Step 4: Sanity Check
Let us check theinstallation by running the following on a newly opened MATLAB window:
```
tbxManager restorepath (I do not have it added to my MATLAB startup)
yalmiptest
```
You will see that YALMIP is able to use GUROBI as the underlying solver for LP/QP, MILP, MIQP, etc. after you run the test function script as shown by the below image:

![image](https://github.com/user-attachments/assets/e2bdd9ba-4c47-48bf-8ea2-4f3cf59a43e0)
