# Grex QuickStart Guide 

## Intended purpose and usage of system

Grex is a legacy system, fist put in production in early 2011. It was primarily intended for applications that can take advantage of non-blocking low latency InfiniBand networks and large memory per compute node. Since April 2, 2018 Grex is available only to the users affiliated with UManitoba.

Grex is a Latin for herd (or flock?).

## Access Conditions

As of the moment, Grex is using the legacy Westgrid account management system affiliated with ComputeCanada user database (CCDB). Thus there are three technical conditions for the access: an active [CCDB](https://ccdb.computecanada.ca) account; Westgrid consortium acount enabled in CCDB ( [there, chose Westgrid](https://ccdb.computecanada.ca/me/facilities) ); and finally an active CCDB role affiliated with UManitoba. 

## Connecting and logging in

To log in to Grex in the text mode, connect to **grex.westgrid.ca** using an **SSH** (secure shell) client. The DNS name grex.westgrid.ca serves as an alias for two login nodes: **bison.westgrid.ca** and **tatanka.westgrid.ca** .

Uploading and downloading your data can be done using an **SCP/SFTP** capable file transfer client. The recommended clients are OpenSSH (providing **ssh** and **scp**, **sftp** command line tools on Linux and MacOS X) and PuTTY/WinSCP/X-Ming or MobaXterm (Windows). Note that since Jun 1, 2014 the original "SSH Secure Shell" Windows SSH/SFTP client is not supported anymore.

Since Dec. 2015, support is provided for the graphical mode connection to Grex using **X2go** . [X2go](https://wiki.x2go.org/doku.php/download:start) remote desktop clients  are available for Windows, MacOS X and Windows . When creting a new Session, please chose either of the supported desktop environment, **"GNOME"** or **"IceWM"**  in the "Session type" menu. The same Westgrid login/password should be used as for SSH text based connections. For now, there is no load balancing support for connections, so while connecting to the host address  grex.westgrid.ca  will work, session suspend/resume functionality might require specifying connection to a physical Grex login node explicitly, using  tatanka.westgrid.ca  or  bison.westgrid.ca correspondingly.

Finally, for graphical mode it is possible to use VNC remote desktop connections to Grex by tunneling them through SSH. After connecting by SSH usual way, do **module load vncworkspace** command on Grex and follow the instructions on how to use the conveninet vncworkspace wrapper over TigerVNC startup commands.

## Interactive work

The login nodes of Grex can be used to compile code and to run (very) short interactive and/or test runs. All the production jobs should be sumbitted in the batch mode, using our Torque resource management system. It is recommended to run longer interactive workloads as Torque interactive jobs (by using **qsub -I** command) rather than on the login nodes;  a few nodes are reserved for the interactive  jobs.

## Batch job policies

The following polices are implemented on Grex.
-    The default walltime is 3 hours.
-   The default amount of memory per processor (pmem parameter) is 256MB. Memory limits are now enforced, so an accurate estimate of memory resource (either in form of mem or pmem parameters) should be provided.
-   The maximum walltime is 21 days for Gaussian jobs and 14 days for all other jobs.
-   The maximum number of processor-days for all currently running jobs for a single user is 2,800 processor-days. (Attempting to exceed that limit will lead to an error message about MAXPS - maximum processor-seconds.)
-   The maximum number of jobs that a user may have queued to run is 2000. The maximum size of an array job is 1000.
-   Users without a RAC award are allowed to simultaneously use up to 300 CPU cores per accounting group.

## General Storage Information

As of May 20, the  storage system of Grex is upgraded to new Lustre 2.9 based on a Seagate Storage Building Block.  Check the status of the upgrade here. The home filesystem stil lresides on  the original Grex on a DDN S2A-9900 storage controlled. Users data on /home and /global/scratch are subject to Westgrid data storage policy. 

-    The /home NFS filesystem is served by an array of low-latency SAS disks on S2A-9900 and is subject to daily backup. 
-    The /global/scratch  paralell Lustre filesystem is distributed over 8 ZFS arrays of 8TB SATA disks. It is intendent to be used as the high-performance, scalable workspace for active projects. It is not backed up and is not intended for long-time storage of users data that is not actively used. Data of the "retired" Westgrid users are deleted.
-    The local node storage as defined by environmental variable $TMPDIR is recommended for temporary job data that is not needed after job completes. Grex nodes have SATA local disks of various capacities (Table below).

## Compiling and Running Jobs

The login nodes can be used to compile code and to run short interactive and/or test runs. All other jobs must be submitted to the batch system. Normally, you would need to chose a compiler suite (Intel or GCC) and, in case of parallel applications, a MPI library (OpenMPI or MVAPICH2). By default, Intel 14.0.2 compilers with OpenMPI 1.6.5 libraries are loaded, so that the corresponding mpicc and mpif90 wrappers are in users PATH. If you want to change that, issue module purge command to unload them, and then use module load to select the combination of the compilers and libraries you need.

As on the other WestGrid systems, batch jobs are handled by a combination of TORQUE and Moab software. For more information about submitting batch jobs, see Running Jobs. Grex now enforces memory limits for the TORQUE batch jobs. Jobs that do not specify memory (mem or pmem parameters in qsub) explicitly, will be assigned the default pmem=256mb value. Note that unlike some of the other Westgrid systems, vmem and pvmem resource requests on Grex should not be used.

The /home file sytem on Grex is not designed for heavy I/O operations. Therefore, it is important that jobs that require significant amount of I/O are not run from /home/<username>. Instead, /global/scratch/<username> should be used all such jobs.
