---
published: true
title: Quick Start Guide
description: Grex HPC machine quickstart guide
---
ntended purpose and usage of system

IMPORTANT: 

This system is defunded since March 31, 2018. Since April 2, 2018 Grex is available only to the users affiliated with UManitoba. Visit the WestGrid Migration page for more information.

Grex is primarily intended for applications that can take advantage of non-blocking low latency InfiniBand networks and large memory per compute node. Grex is a general-use system so no special access requests required for registered WestGrid users.

Grex is a Latin for herd (or flock?).
Request for Access

As of the moment of writing (May 2018), there are three conditions for the access: an active CCDB account; Westgrid consortium acount enabled in CCDB; and an active CCDB role affiliated with UManitoba.
Connecting and logging in

To log in to Grex in the text mode, connect to grex.westgrid.ca using an SSH (secure shell) client. The DNS name grex.westgrid.ca serves as an alias for two login nodes: bison.westgrid.ca, tatanka.westgrid.ca

Uploading and downloading your data can be done using an SCP/SFTP capable file transfer client. The recommended clients are OpenSSH (providing ssh and scp, sftp command on Linux, MacOS X) and PuTTY/WinSCP/X-Ming (Windows). Another alternative for Windows is a shareware code Mobaxterm. Note that since Jun 1, 2014 the original "SSH Secure Shell" Windows SSH/SFTP client is not supported anymore.

Since Dec. 2015, support is provided for graphical mode connection to Grex using X2go remote desktop client that are available for Windows, MacOS X and Windows on the X2Go website . When creting a new Session, please select either "GNOME" or "IceWM"as the desktop environment in "Session type" X2go menu, as this is the one that is available on Grex and seem to work best. The same Westgrid login/password should be used as for SSH text based connections. For now, there is no load balancing support for connections, so while connecting to the host address  grex.westgrid.ca  will work, session resuming might require specifying connection to a physical Grex login node explicitly, using  tatanka.westgrid.ca  or  bison.westgrid.ca correspondingly.

Finally, for graphical mode it is possible to use VNC remote desktop connections to Grex by tunneling them through SSH. After connecting by SSH usual way, do '' module load vncworkspace  '' command on Grex and follow the instructions on how to use the conveninet vncworkspace wrapper over TigerVNC startup commands.
Batch job policies

The following polices are implemented on Grex

    The default walltime is 3 hours.
    The default amount of memory per processor (pmem parameter) is 256MB. Memory limits are now enforced, so an accurate estimate of memory resource (either in form of mem or pmem parameters) should be provided.
    The maximum walltime is 21 days for Gaussian jobs and 14 days for all other jobs.
    The maximum number of processor-days for all currently running jobs for a single user is 2,800 processor-days. (Attempting to exceed that limit will lead to an error message about MAXPS - maximum processor-seconds.)
    The maximum number of jobs that a user may have queued to run is 2000. The maximum size of an array job is 1000.
    Users without a RAC award are allowed to simultaneously use up to 300 CPU cores per accounting group.

Interactive jobs

The login nodes can be used to compile code and to run very short interactive and/or test runs. All the production jobs should be sumbitted through Torque. It is recommended to run interactive workload as Torque jobs as well (by using qsub -I command); there are a few nodes reserved for such jobs.

 
General Storage Information

As of May 20, the  storage system of Grex is upgraded to new Lustre 2.9 based on a Seagate Storage Building Block.  Check the status of the upgrade here. The home filesystem stil lresides on  the original Grex on a DDN S2A-9900 storage controlled. Users data on /home and /global/scratch are subject to Westgrid data storage policy. 

    The /home NFS filesystem is served by an array of low-latency SAS disks on S2A-9900 and is subject to daily backup. 
    The /global/scratch  paralell Lustre filesystem is distributed over 8 ZFS arrays of 8TB SATA disks. It is intendent to be used as the high-performance, scalable workspace for active projects. It is not backed up and is not intended for long-time storage of users data that is not actively used. Data of the "retired" Westgrid users are deleted.
    The local node storage as defined by environmental variable $TMPDIR is recommended for temporary job data that is not needed after job completes. Grex nodes have SATA local disks of various capacities (Table below).

Storage Information on Grex
Directory path 	Size 	Quota 	Command to check quota 	Purpose 	Backup Policy
/home 	5 TB 	30 GB/user ; 0.5M files/user 	quota 	

Home directories
	

Daily backup
/global/scratch 	418TB 	2048 GB/group ; 1M files/user 	lfs quota -h -u $USER /sbb 	

Global Scratch
	

No backup. The /global/scratch is intended as a workspace for active projects; long-time data retention is not guaranteed.
$TMPDIR 	Between 150GB-1.8TB per compute node 	Mostly under 1TB, few nodes with 1.8TB 	Request space when submitting job (-l file=size) 	

Node-local scratch
	

Deleted when the job is completed
Program Information on Grex
Compiling and Running Jobs

The login nodes can be used to compile code and to run short interactive and/or test runs. All other jobs must be submitted to the batch system. Normally, you would need to chose a compiler suite (Intel or GCC) and, in case of parallel applications, a MPI library (OpenMPI or MVAPICH2). By default, Intel 14.0.2 compilers with OpenMPI 1.6.5 libraries are loaded, so that the corresponding mpicc and mpif90 wrappers are in users PATH. If you want to change that, issue module purge command to unload them, and then use module load to select the combination of the compilers and libraries you need.

As on the other WestGrid systems, batch jobs are handled by a combination of TORQUE and Moab software. For more information about submitting batch jobs, see Running Jobs. Grex now enforces memory limits for the TORQUE batch jobs. Jobs that do not specify memory (mem or pmem parameters in qsub) explicitly, will be assigned the default pmem=256mb value. Note that unlike some of the other Westgrid systems, vmem and pvmem resource requests on Grex should not be used.

The /home file sytem on Grex is not designed for heavy I/O operations. Therefore, it is important that jobs that require significant amount of I/O are not run from /home/<username>. Instead, /global/scratch/<username> should be used all such job
