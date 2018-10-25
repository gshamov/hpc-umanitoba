# QuickStart Guide for New Users
## Table of Contents

    About this QuickStart Guide - Intended audience for this QuickStart Guide
    Getting Started - Recommended steps to begin using WestGrid and Compute Canada
    Choosing Which System to Use - Overview of WestGrid's hardware and software resources
    Setting up Your Computer - Software to install on your computer to access WestGrid systems
    Connecting and Logging In - Using a terminal client to log in
    Working Interactively - UNIX commands, editing and managing files
    Software - Finding installed software or requesting software
    Programming - Porting and compiling software
    Running Batch Jobs - Using the main WestGrid computing resources
    Compute Canada Cloud - National cloud computing resources
    Post-Processing - Visualization and data archiving
    Cloud Storage - Using WestGrid's ownCloud service
    Usage Guidelines - Account limits and usage hints
    Account Passwords - Password info including password resets
    Getting Help - How to contact WestGrid's support team

 
## About this QuickStart Guide

This QuickStart Guide is intended to provide new users with basic information to start using WestGrid and Compute Canada resources. It consists primarily of links to other pages on the WestGrid website. We recommend that you review all of the topics on this page, and explore the links to more detailed information on the subjects that are most relevant to you. If you have questions at any point during your account setup process or as you begin to use the resources, please contact support@westgrid.ca - no question is too big or small!

If you would like more a more general overview of the organization and its services, please refer to our FAQ for Prospective Users, or WestGrid Backgrounder or our Conditions of Use page.

View or download our 2-page guide on Getting Started with WestGrid and Compute Canada.

 
## Getting Started

To use WestGrid resources, you must first complete a two-step application process:

    Register in the Compute Canada DataBase (CCDB)
    Apply for a WestGrid account

Important Note: If you are a graduate student, postdoctoral fellow, research assistant, undergraduate student, non-research staff member, visiting faculty or external collaborator, you will need to be sponsored by a Principal Investigator (PI), i.e. a university faculty member. The PI must register in the CCDB first, and then he / she can sponsor you as a 'Group Member' under his / her account. More detailed instructions for applying for a WestGrid account can be found here: Registering with the CCDB and WestGrid

Once your application for a WestGrid account has been approved, you will receive a confirmation email and you can begin using the computing and data storage facilities. 

 
## Choosing Which System to Use
### National Resources

WestGrid's computing facilities are part of Compute Canada's national platform of advanced research computing resources. New national sites offer expandable and modern data centres with highly qualified personnel. Operations of the new systems are delivered through national teams, drawing upon regional and local expertise distributed across Canada. Please refer to the CC User Documentation wiki for more information on national systems and services.

**Instructions for Getting Started with the National systems can be found here.**
### WestGrid Legacy Systems

Please note that most WestGrid systems have been defunded. For details about this process, as well as key information and instructions for WestGrid users, visit our Migration Process page.  
Factors to Consider

There are a number of factors to consider when choosing a system, the most important typically being whether or not your job runs in parallel and the amount of memory required per process. If the job can be run in parallel, an important criterion to use in determining where to run it is whether it can make use of multiple cluster nodes (such as when using MPI) or has to be run on a shared-memory machine (such as when OpenMP is used). Some general guidelines are:

-    Small-memory serial jobs (jobs that use one core) or undemanding parallel jobs may be run on several of the clusters, including Cedar and Orcinus.
-    Researchers with large-memory serial jobs are usually directed towards a system with the least memory per node that can accomodate the work while still allowing for the possibility of other user's jobs running simultaneously on the same compute node.  The definition of "large" is under debate, but, for jobs requiring more than a few GB of memory, it could be worthwhile discussing options with WestGrid support at support@westgrid.ca.
-    OpenMP-based parallel jobs (which run only on single nodes) can be run on many systems, but generally do better on systems that have relatively large amounts of memory accessible on a single node like the national system Cedar.
-    For MPI-based parallel programs requiring a high-performance interconnect try the Orcinus or Cedar cluster.  The memory per process and storage requirements may influence our advice on which system to use.  The new systems have large associated storage facilities.
-    A commercial license for the Gaussian Chemistry software is only available on the Cedar cluster. In other cases, availability of certain software libraries may dictate the system to use, but, it may be possible to work around such issues by installing additional software or substituting one library for another. See the main WestGrid software page for tables showing the installed software on WestGrid systems, including information about the operating system and compilers.

For a comparsion table of WestGrid's various systems, see the Computing Facilities page. Or, for links to details about the computing facilities available through WestGrid, visit the QuickStart guides.
 
## Setting up Your Computer

To connect to and work with WestGrid systems you may have to install one or more software packages on your own computer. Although web browser-based tools may become available for accessing WestGrid in the future, especially as grid services are developed, most users will continue to log in and work directly on remote systems for some time to come.
### Terminal client supporting ssh

The most important piece of software you will need is a terminal (client) program that supports the secure shell (SSH) protocol for network communications to remote servers. Linux and Mac OS X users can typically use the built-in terminal programs, whereas Microsoft Windows users often install an additional SSH client, such as MobaXterm or PuTTY. MobaXterm is available from http://mobaxterm.mobatek.net. PuTTY can be obtained from http://www.chiark.greenend.org.uk/~sgtatham/putty/ . There is an extensive list of SSH clients at http://en.wikipedia.org/wiki/Comparison_of_SSH_clients . MobaXterm has the advantage of providing a built-in graphical file transfer program and X Window display server (see below).
### File transfer client supporting scp and sftp

You will also need software that supports secure transfer of files between your computer and the WestGrid machines. The command line programs scp and sftp can be used from within terminal programs on Linux or Mac OS X computers. On Microsoft Windows platforms, similar programs, pscp and psftp come with PuTTY.  WinSCP is a free file transfer program for Microsoft Windows that offers a graphical interface, as does MobaXterm.
### X Window display server for graphics

To use graphical programs on WestGrid computers and show the results on your monitor, you will need to run an X Window display server (X server) program on your local computer. You start up such a program and leave it running in the background while using your ssh terminal program. When graphics commands are relayed by your ssh client from the remote WestGrid computer to the X Window display server, it will display the appropriate graphics on your screen. Your keyboard and mouse commands can be relayed in the other direction and passed from your ssh client to the graphics program running on the remote system. The process is called X11 tunnelling or forwarding. For this to work, you should look for an option in the settings or preferences of your ssh client program to turn on X11 tunnelling.  See the WestGrid remote visualization page for more details.

Commercial X Window display servers are available, but, most users can get by with free programs. Linux users will find the X Window support already installed with most distributions. Modern versions of Mac OS X ship with a program called X11, which is not installed by default but is on the system disks. Most recent versions of OS X do not ship with X11. You need to get it from XQuartz. One option for Microsoft Windows users is to install Xming. If installing Xming, you should also install the optional font package. If your graphics hardware does not work well with Xming, you could try Xming-mesa, from the same site. If you have chosen MobaXterm for your terminal program, then, you could try the built-in X Window display server that is provided with that program.

 
### Connecting and Logging In

To connect to a WestGrid system, start your ssh client and specify the host name of the chosen system and your user name in the connection dialogue box or on the ssh command line, depending on what type of ssh program you are using. Each WestGrid machine to which you can connect has an Internet address of the form machine_name.westgrid.ca. So, for example, to connect to Orcinus from a command-line ssh program, you could type:

    ssh your_username@orcinus.westgrid.ca

If your user name on your local system is the same as on WestGrid, you may omit it and to connect to Orcinus simply type:
ssh orcinus.westgrid.ca

Please note that it may take a day or so before your account is ready to use.  

If your connection attempt is refused, even after waiting a day for your account to be set up, please write to support@westgrid.ca and tell us the IP address of your machine, the name of the WestGrid system to which you are trying to connect and the user name you have entered. You can visit http://westgrid.ca/iptest with a web browser on your machine in order to determine your IP address.  (Please ignore any warnings you may see regarding Domain Name System (DNS) registration).

To start a session with X11 forwarding turned one can typically use
ssh -X orcinus.westgrid.ca

although from Mac OS X systems, you may have to use
ssh -Y orcinus.westgrid.ca

If you have successfully connected to one of the WestGrid login servers, you will be prompted for a user name and password. The user name is not your full name, nor your email address, but, is the 2- to 8-character name that was entered in the "Requested Username" box when you applied for a WestGrid account. The password to use is the one you specified on that form also. Your username and password are the same on all WestGrid machines.
Initially, both will have the values you requested on your account application, although the password can and should be changed regularly. For security, passwords are stored using one-way encryption and cannot be recovered. As well, passwords should never be transmitted via email and WestGrid staff will never request your password nor send you one via email. Refer to the Password page for instructions on resetting your password.

 
## Working Interactively

The hardware at most of the WestGrid sites is set up with one or more servers to which users have direct login access, with the main computational clusters being accessed indirectly, by submitting batch job scripts. The batch jobs run non-interactively when the scheduling system is able to find a time slot with the computational resources needed for the job. However, interactive sessions are typically needed to prepare the batch scripts and input files, compile and debug programs, manage data and post-process results. Some guidelines for working interactively are given in this section.
### The UNIX environment

Each of the WestGrid computers runs some version of the UNIX (or Linux) operating system. The program that responds to your typed commands and allows you to run other programs is called the UNIX shell. Examples of a UNIX shell are bash and tcsh. It is useful to have some knowledge of the shell and a variety of other command-line programs that you can use to manipulate files. If you are new to UNIX systems, we recommend that you work through one of the many online tutorials that are available, such as the UNIX Tutorial for Beginners provided by the University of Surrey. The tutorial covers such fundamental topics, among others, as creating, renaming and deleting files and directories, how to produce a listing of your files and how to tell how much disk space you are using.

The UNIX man command (man for "manual") can be used to get information about other commands. For example, a reference page about the ls command, for listing file names and properties, can be displayed by typing:
man ls

The default environment varies from one WestGrid system to another and also depends on which UNIX shell you selected on your WestGrid account application form. The working environment is partially determined by the commands in one or more startup files that are automatically executed every time you log in. For bash shell users, these files may include .bashrc and .bash_profile. For tcsh users, .login and .cshrc are executed. You can customize your environment by editing these files to change such things as the appearance of the shell prompt (the characters that appear at the start of the line when the shell is waiting for you to type a command) and the command path (a list of directories in which the shell will search for commands). Use caution when modifying these files, as inappropriate changes may prevent you from being able to work on the system.

Please note that binary executable files from Microsoft Windows PCs will not run on the WestGrid systems. In order to work with such programs, you must obtain the source code and recompile for use on UNIX or Linux. Not all programs will have such source code available.
### File systems

As on other computer systems, in a UNIX environment there is a file system that provides a hierarchy of directories (called folders on some other systems) for storing files. When you log in, you are working in part of the file system called your home directory. You may create files and subdirectories in your home directory, although on some WestGrid systems there is a quota limiting the amount of space you can use. How you organize your files is up to you, but, it might be helpful to create a separate subdirectory for each job that you submit and to have a separate directory for program source code.

When naming files and directories, you will find it easier to navigate the file hierarchy and to reference files in UNIX commands if you do not use spaces in file names. Also, keep in mind that UNIX is case sensitive in most situations, so, for example, Nobel_Prize.exe and nobel_prize.exe refer to different files. Another difference between UNIX and Microsoft Windows environments is that a file suffix, if present, is of no particular significance to the basic UNIX file manipulation commands. So, for example, there is no requirement for executable programs to have an ".exe" suffix.

Besides your home directory, on most of the WestGrid systems there are additional places (/tmp, /scratch and /global/scratch among others) where you can store files and from which you can run programs. Some file systems have more space than others. Sometimes there are performance reasons for choosing one location vs. another. There may also be different usage policies (how long you can keep files and how big they can be) for the various file systems. See the QuickStart guide for the particular system you are using for more information or write to support@westgrid.ca for advice.
### Transferring files

When just starting out on WestGrid systems, you will likely have source code or data to be transferred from your own computer or one at your own institution. Similar to the requirement for a terminal program supporting SSH (Secure Shell), WestGrid requires that you use file transfer software that supports SCP (Secure Copy) or SFTP (SSH File Transfer Protocol). Most ssh packages come with additional programs to support these secure file transfer methods.

Once you have files on a WestGrid system, you can move them between directories using the UNIX mv command.  This is sometimes necessary, for example, when moving output files from a scratch location (a temporary directory used for files actively being used by running jobs) to a more permanent location.

Files can be moved between systems using scp or sftp command line tools.  If you prefer a graphical interface, Globus can be used for transfers between WestGrid systems, between WestGrid and the Compute Canada National Data Cyberinfrastructure (NDC) and between your own computer and these central storage services.

While not specifically related to file transfer, you should consider using the National Data Cyberinfrastructure for long-term file storage.  For more on comments on data storage, see the Storage Overview page.

One thing to be aware of when transferring files is that there are different conventions for the characters that terminate each line in a text file on UNIX/Linux, Microsoft Windows and Macintosh computers. File transfer software typically has a transfer mode in which line-ending conversion is done automatically. For example, in Microsoft Windows-based programs, files that have a .txt suffix would be treated as text files for which conversion would likely be done, but, C or Fortran source code files having names ending in .c or .f, respectively, might not be recognized as text. You may have to configure your file transfer software to correctly handle files that you commonly use.
### Editing files

For creating and editing files such as job scripts or source code, new users may choose to manipulate the files on their local computer and then transfer them to a WestGrid system for use. Alternatively, the login nodes of WestGrid systems offer well-known text-based editors such as Emacs and vi. Graphical editors are also available if your computer is set up with X Windows software as described above. For example, the NEdit editor is a graphical editor with similar keyboard shortcuts to what would be found on PCs. See the next section for comments about running NEdit and other interactive programs. There are several editors available for you to use, as shown on the software page (filter by "Files and Data").

There are also a number of UNIX commands available for looking at the contents of files. For example, to page through an output file, test.pbs.o31416, the more command can be used:

more test.pbs.o31416
### Running interactive programs

To run a program on a UNIX system, type the name of the corresponding executable file on the command line at the shell prompt. The UNIX shell searches for the command only in the directories in a list stored in a variable, PATH. You can see this list by typing:
echo $PATH

If you get a "command not found" error, check for a spelling mistake or a letter typed in the wrong case, or confirm that the directory containing the executable file is in your command path. On some WestGrid systems, the current working directory is not part of the default command path. In such a case, you can either change the PATH or type "./" in front of the command, as in:
./my_command

This instructs the shell to execute the program "my_command" located in the current working directory ("./").

Many programs (including UNIX commands), take additional arguments, such as numerical parameters or file names, which are listed on the command line after the name of the executable program. Often the command-line arguments are preceded by a dash. For example, to list the last 40 lines of the file, geometry.in, you could use the UNIX tail command:
tail -40 geometry.in
### Restrictions on interactive jobs

Since the servers to which you log in are shared by many users, interactive work on those machines should be limited to activities such as editing files, compiling programs or running small, short, tests of your program. The memory and number of processors varies among the login servers, so, the exact policy on the length and size allowed for test runs varies from machine to machine. On some systems there are special queues with short time limits that are intended for batch jobs for testing and debugging. It is also possible to submit a placeholder batch job to reserve one or more dedicated processors, which may then be used for interactive work, without interferring with other users' jobs. See Working Interactively for more information.

 
## Software
### Compute Canada's National Systems software

For information on software available on Compute Canada's national systems please refer to the Available Software page on the Compute Canada User Documentation wiki. 
### Locating installed software

Installed software on WestGrid systems includes the UNIX or Linux operating system and a number of standard utilities that often come with such systems. A number of major commercial and free software packages are also available, as well as compilers and a variety of numerical, graphics and file-manipulation libraries for researchers compiling their own codes. Refer to the main WestGrid software page for details on which packages have been installed on each of the main computational systems. The installation directories have not been standardized, so, please refer to the table at the top of the software page for a list of the directories where software is typically installed on each system.

For many installed software packages, usage instructions include a reference to loading a module file to configure aspects of the run-time environment, such as setting the search path for the associated binaries and libraries.  If there are multiple versions of a package installed, the module command is often used to choose which version to use.  More information about modules is available here.
Installing your own software

You are welcome to install software under your home directory (if the software license allows the software to be used on remote machines that are not under your direct control and which may not be at your home institution). If you need to share a software package with other members of your group, a corresponding UNIX group can be created to control access to the software. Write to support@westgrid.ca for details on how to do this.

See the programming section below for information on compiling your code.
### Requesting software installation

If a package was installed for testing or at the request of a limited number of researchers, it may not be listed on the software page. If there is a package that you need, there is a chance that it has already been installed but not announced. 

Commercial software can be requested through an online form.
### Software licensing

Although WestGrid has purchased some commercial software, such as the Gaussian chemistry code, there are other packages, such as ABAQUS and MATLAB being run on WestGrid systems using licenses provided by WestGrid institutions, rather than WestGrid itself. There are often limitations on such licenses, in terms of where the software may be run and how many simultaneous copies may be used.

 
## Programming

A general introduction to programming on WestGrid systems is given elsewhere. That page including links to such things as parallel programming tutorials and to a series of pages giving examples of using the main compilers on all the WestGrid systems. Tables on the software page list all the compilers and the numerical (and other) libraries available to link with your code.

If you have used non-standard language features in your code you may need to make some changes in order to get it to run on WestGrid systems. Trying your code with more than one compiler is recommended, as this helps identify non-portable sections of your code that should be improved. Write to support@westgrid.ca if you would like help in porting, debugging or optimizing your code.

Sometimes researchers have chosen to use WestGrid because they want to increase the size of the problem being studied. Running the code on larger data sets can sometimes uncover performance issues or memory access problems. If the code was previously run only on a 32-bit system, moving to a 64-bit environment may require changes if inappropriate assumptions were made regarding the size of some data types, for example.

Another issue that arises when tackling larger problems is the length of time required for the calculation. Some WestGrid systems have job time limits as short as one day. It is recommended that you design your program to include a checkpoint and restart capability. That is, you should periodically write out enough data so that your program can be restarted, if necessary, by reading in that data. That way you can avoid losing the entire calculation if the program doesn't finish before the job time limit is reached.

 
## Running Batch Jobs
### National Systems

IMPORTANT NOTE: The new Compute Canada systems (available summer 2017) do not use the Moab/TORQUE job submission systems. Instead they use Slurm, which requires a different format. Please see the Compute Canada Running Jobs documentation for details.

The following information is only for WestGrid legacy systems.
### The batch environment

As mentioned above, the main WestGrid computational clusters are accessed by submitting batch job scripts from a login server. It is usually not necessary (and in some cases not allowed) to log on to the compute nodes directly. The system software that handles your batch job consists of two pieces: a resource manager (TORQUE) and a scheduler (Moab). Documentation for these packages is available through Adaptive Computing. However, typical users will not need to study those details.
Batch job scripts

Batch job scripts are UNIX shell scripts (basically text files of commands for the UNIX shell to interpret, similar to what you could execute by typing directly at a keyboard) containing special comment lines that contain TORQUE directives. TORQUE evolved from software called PBS (Portable Batch System). Consequences of that history are that the TORQUE directive lines begin with #PBS, some environment variables contain "PBS" (such as $PBS_O_WORKDIR in the script below) and the script files themselves typically have a .pbs suffix (although that is not required).

There are small, but, significant differences in the batch job scripts, particularly for parallel jobs, among the various WestGrid systems. Examples for each system, for both serial and parallel jobs are given in the programming documentation. So, if you begin working on one WestGrid system and switch to another, refer to the documentation before submitting jobs on the second system.

Here is an example job script, diffuse.pbs, for a serial job to run a program named diffuse.
<code>
#!/bin/bash
#PBS -S /bin/bash

# Script for running serial program, diffuse.

cd $PBS_O_WORKDIR
echo "Current working directory is `pwd`"

echo "Starting run at: `date`"
./diffuse
echo "Job finished with exit code $? at: `date`"
</code>

### Commands for submitting, monitoring and deleting jobs

To submit the script, diffuse.pbs, to the batch job handling system, use the qsub command:
qsub diffuse.pbs

If a job is expected to take longer than the default time limit (typically three hours) or uses more than the default memory, additional arguments may be added to the qsub command line. If diffuse is a parallel program, you also have to specify the number of nodes on which it is to run. For example:
qsub -l walltime=72:00:00,mem=1500mb,nodes=4 diffuse.pbs

Please see the Running Jobs pages or QuickStart guides for the individual WestGrid systems for more information about the walltime, memory and node limits for specific machines.

When qsub processes the job, it assigns it a job ID and places the job in a queue to await execution. To check on the status of all the jobs on the system, type:
showq

To limit the listing to show just the jobs associated with your user name, type:
showq -u username

To delete a job, use the qdel command with the jobid assigned from qsub:
qdel jobid

On some WestGrid systems it is difficult to directly monitor some aspects of a job's progress, so, it is a good idea to make sure that your program periodically writes output to a file. You can then check the contents of that file to see how the program is doing. In other cases, such as when you need to confirm how much memory your job is using, you may have to write to support@westgrid.ca to request that an administrator check on the job for you.

Please see the Job Monitoring page for more information on commands that can be use to monitor job queues and machines.
### Rapid Access to Batch Computational Resources

Compute Canada operates large shared computing facilities on which computational “jobs” are scheduled via a priority-setting mechanism known as “fair share”. Each year Compute Canada allocate roughly 80% of the available compute cycles via formal Resource Allocation Competitions (RAC) and leaves roughly 20% for its Rapid Access Service. Unlike the RAC process, Compute Canada's Rapid Access Service is not a guaranteed allocation of certain computational resources. It is a shared pool of unallocated resources. These resources are available for “opportunistic use” to anyone with an active Compute Canada account. For more information on the Rapid Access Service, including core-years available per system, please visit the Compute Canada website.

## Compute Canada Cloud

The Compute Canada Cloud service responds to researchers who have a need for greater configurability, availability, durability or portability than may be available on non-cloud systems or clusters. By using virtual machines (VMs) you configure through your cloud account, you can customize the computing environment to meet your unique needs. Carry out both data and computationally intensive work easily. Use the Compute Canada cloud to build portals and platforms, or to handle data that you’re scraping from the web. Then share your work with your other devices, your team or other collaborators. For more information on this cloud service, and to register for a Cloud account, please visit the Compute Canada website.
 
## Post-Processing

After having completed some calculations on the WestGrid machines, most researchers will need to post-process some output files.
Managing files

In some cases, after a preliminary examination of the output, there be a way to reduce the volume of data by extracting key numbers and then discarding some of the output. The UNIX grep utility may be helpful in simple cases. A more elaborate process using shell scripts or other programs may be needed. Once the data have been consolidated, files should be backed up, either by transferring them to your own computer or by using the National Data Cyberinfrastructure, as mentioned in the section on transferring files, above. If you have a large number of small files, you should consider combining and compressing them with the tar and gzip programs.
## Visualization

For most types of calculation, graphical display of the output can be useful for identifying bugs in programs, to help interpret the data and to summarize the results for others. WestGrid has hardware and software at one site specially geared toward remote visualization, however, it is possible to use visualization tools on any of the WestGrid systems. Graphical data analysis needs tend to be quite specific, so, you are encouraged to discuss your particular project with WestGrid support analysts. In some cases it may be feasible to produce graphs or images in batch mode and in other cases, where more interactivity is required, we may recommend using the WestGrid visualization server or transferring the data back to your own computer for visualization there.

 
## ownCloud Storage

WestGrid provides access to ownCloud, a Dropbox-like cloud storage service, for all WestGrid users. You can use your WestGrid username and password to login to our ownCloud server and all data transfers between local devices and WestGrid's ownCloud are encrypted. More detailed information for setting up your ownCloud account and getting started can be found on our Cloud Storage page. Some starter tips are included below.
### Using WebDAV Clients

In general, you can use any WebDAV clients to "mount" an ownCloud folder to your desktop using WebDAV URL https://owncloud.westgrid.ca/remote.php/webdav/. Once mounted, you can drag and drop files between the WebDAV drive and your local desktop.

Mac OSX: Select Go -> Connect to the Server, enter the WebDAV URL for the Server Address, and click Connect. You will be asked for your username and password to login. After authentication, you will see a WebDAV drive on your desktop.

Windows: Although Windows 7 can mount WebDAV natively, we do not recommend this method due to performance reasons. Consider using Cyberduck or other clients instead.

Linux: There are many WebDAV applications available for Linux, please consult the ownCloud user manual for recommendations.
Sharing Files Using ownCloud

Any file/folder on ownCloud can be shared to download with a local user, group or any person online with a public link. Sharing and document editing can be done securely in the browser and be shared inside ownCloud or via a public link. Users that have an account on the same server can be invited or public invitations can also be sent be email. Sharing options also enable users to share via a public link, for which you can set a password to prevent editing by unwanted users. Shares can also have an expiration date that will expire the link after a given date. For more information on sharing files using ownCloud, please visit our Cloud Storage page.
### Using UNIX Command Line Tools

You can also use any available WebDAV command line clients, like curl and cadaver, to copy files between your host and ownCloud. Command line tools are useful when you copy data between a remote host you login to and ownCloud. cURL is usually installed on Mac OSX and Linux systems and can be used to upload and download files using an URL. For more detailed instructions on this, please visit our Cloud Storage page.

 
## Usage Guidelines
### Job limits

WestGrid and Compute Canada are comprised of a wide range of hardware types, from single node large shared memory machines to clusters consisting of many dual-processor small-memory nodes. The maximum time limit allowed, the maximum number of processors that may be requested, the maximum number of jobs that can run simultaneously, etc. have been set by system adminstrators based on the characteristics of the machines and the role they play in the WestGrid / Compute Canada environment. Generally speaking, jobs that request more resources (processors or memory) will have more strict limits than jobs that use less.
### How much is reasonable?

In general, you may submit as many jobs as you like as the batch scheduling system will restrict the number that are run at any given time. However, so as not to unnecessarily burden the scheduling system or alarm other users, in most cases you should stage job submission so that you don't have many weeks of work waiting to run. It would be reasonable to submit some tens of jobs, for example, if they last a few days each, or hundreds of jobs if they are only a few hours long. You should plan to monitor your runs regularly.

Users are also expected to take some responsibility for ensuring that their jobs are running efficiently, through the use of appropriate algorithms and compiler optimization options and linking to optimized libraries when possible. Programs should be tested on small problems before committing to longer runs using more resources. In general, parallel programs run more efficiently on smaller numbers of processors. So, study how the performance of your code depends on the number of processors used and balance the need for quick turnaround of your jobs with overall efficiency (that is, use small numbers of processors unless you have a good reason not to).
### Compute Canada fairshare policy

Generally speaking, Compute Canada allocates its batch processing priority based on a fairshare algorithm. Each user is allocated a share of the total system resources, which effectively translates into priority access to the system. If you have used a large fraction of the system recently (ie. larger than your fair-share), your priority drops. However, the scheduling system has a limited time window over which it calculates priority. After some time (e.g., weeks) of reduced usage, it gradually “forgets” that you overused in the past. This is designed to ensure full system usage and not to penalize users who take advantage of idle compute resources. A consequence is that your total allocation is not a limit on how many compute resources you can consume. Rather, your total allocation represents what you should be able to get over the course of the year if you submit a constant workload to the system and it is fully busy. In other words, once your “total allocation” is used, just keep working.
### Job priorities

Users are sometimes concerned that their jobs may not be progressing in the queue relative to other users. There are a number of factors that affect the priority of the jobs waiting to run. The basic mechanism for determining the priority is called fairshare in which target usage amounts are assigned to each project. When considering which jobs to run, the scheduling software takes into account the past history (typically over a time span of a couple of weeks, with more recent usage weighted more heavily) and compares the amount of processing completed to the target. Priorities of the jobs are raised or lowered so as to try to meet the fairshare targets.
### Resource Allocation Competitions (RAC)

Each year Compute Canada allocate roughly 80% of the available compute cycles via formal Resource Allocation Competitions (RAC) and leaves roughly 20% for its Rapid Access Service (“opportunistic use” for anyone with an active Compute Canada account). Applications submitted to the RAC are evaluated for both technical feasibility and scientific excellence. These competitions are open to all researchers based at Canadian academic institutions who are eligible to apply for funding to the federal granting agencies. For more information on the annual RAC process, visit the Compute Canada website.
### Accounting

Project usage statistics are available for viewing by project members by logging on to the Compute Canada Database (CCDB).

 
### Password Recovery

A WestGrid account gives you an ID (username) which is valid for use with all of the WestGrid facilities. When you are given an account, an ID is set up for you at each of the sites, and a GridCanada certificate is issued for you. All of these use the password you selected. For security reasons, no one at WestGrid knows your password. 

If you have forgotten your password and do not have security questions on file, you will have to reset your password by contacting the Accounts team. If you have forgotten your password and you have the security questions on file, you can click the Forgotten Password page link on the portal sign in page. You will immediately receive an email with a URL. Please note that the URL will only be valid for one hour.

More information on passwords can be found on the Passwords page under the User Accounts section.

 
### Getting Help

Beyond this guide, there are a number of resources you can use to get help with WestGrid. These include:

-    WestGrid Support Team- Email support@westgrid.ca for any kind of support question, such as account or connection problems, advice on system characteristics or which WestGrid system to use, debugging, optimization, parallelization or other programming issues, software enquiries, visualization or data management advice, etc. See the main WestGrid support page for an overview of technical support and hints about navigating through the site. Visit the Site Leads page to find the WestGrid Support Team Leader at your insitution.
-    Compute Canada National Systems Support - For help with using any of the national compute or data storage systems please email support@computecanada.ca or visit the Compute Canada User Docs wiki for technical information. You can also visit the Compute Canada website www.computecanada.ca for important news and updates for users.
-    User Training and Seminars - During the fall and winter, WestGrid offers a series of seminars and workshops through video conferencing and web streaming. Past topics have included an overview of WestGrid facilities, introduction to UNIX, serial and parallel (OpenMP and MPI) programming, submitting jobs and data visualization. See the WestGrid Training and Seminars page for the schedule and list of topics in the next seminar series.
-    WestGrid Newsletter and Updates - Our monthly newsletter features timely community updates, upcoming events, and profiles on WestGrid users. View the most recent and archived newsletters here or sign-up to be added to our mailing list and receive your own copy each month. Follow us on twitter @WestGrid to receive real-time updates on WestGrid and HPC news and events, and follow @WGSystems to receive system notifications and status updates for WestGrid's computing and data storage facilities.

