# Globus File Transfer User Guide

Globus is a fast, reliable high-performance service for secure data movement provided by Computation Institute, University of Chicago, Argonne National Laboratory. Designed specifically for researchers, Globus advertises easy-to-use interface with background monitoring features- the service automates the activity of managing file transfers between any two resources - whether between two WestGrid resources or to/from WestGrid and another machine, such as another supercomputing facility, cloud resource, campus cluster, lab server, desktop or laptop.

Globus leverages GridFTP for its transfer protocol but shields the end user from complex and time consuming tasks related to GridFTP and other aspects of data movement.

Globus significantly improves transfer performance by auto tuning the transfer for the users and reduces the time spent managing transfers. Users have reported 10x or even 100x improvements over other transfer methods such as SCP.

When it originally launched, Globus' website was branded Globus Online. If you see references to Globus Online, they are referring to the Globus website.
## Using Globus 

Globus can be used for moving data between any two resources, whether it is a small number of very large (even terabyte-sized) files or a very large number of small files. Note: A resource is represented in Globus as an "endpoint", identified by a unique name (for example, Simon Fraser University's Bugaboo is computecanada#bugaboo). For many small or uncomplicated transfers, scp, or WestGrid’s grid-enabled gcp, will work perfectly well.

You might choose to use Globus when:

- You want to use a graphical user interface (GUI) to transfer data between WestGrid resources/systems.
- You want file transfer management (“fire and forget”):
-- monitoring and auto-tuning performance
-- retrying failures
-- recovering from transfer faults automatically where possible
-- reporting status
- You want performance better than single-stream scp to/from a non-WestGrid resource to a WestGrid resource, without having to configure GridFTP and Globus Toolkit tools manually. Globus transfers can be many times faster than scp for large data sets.

## Specific use cases

- Moving data between WestGrid resources: Globus can be used to move data between any two WestGrid resources. All WestGrid resources are already configured as Globus endpoints.
- Moving data to WestGrid from a local machine (or vice versa): For cases where a user is looking to upload or download files to/from an WestGrid resource to a user's machine, Globus provides a simple mechanism to setup and manage such transfers. The phrase "user's machine" refers to any machine on which a user has an account such as a personal laptop, a campus server, or a machine used to access data from an instrument. Globus makes it possible to easily transfer to and from any machine (even if behind a firewall or NAT without any administrative privileges) with just a few clicks and without the typical difficulties of a GridFTP install.
- Moving data between two non-WestGrid machines: Globus can also be used to move data between a campus cluster, a non-WestGrid computing facility, or a personal machine. Visit the Globus Connect Personal site for step-by-step instructions on how to turn your machine into an endpoint.

## Getting started with Globus Online

### Accessing Globus

Register for a Globus account at the Globus site.

### Transferring Files

- Moving data between WestGrid resources
- Moving data to WestGrid from local machine (or vice versa)

### Moving data between WestGrid resources

- Create a Globus account by visiting https://www.globus.org/SignUp if you have not done so already.
- To transfer files go to https://www.globus.org/xfer/StartTransfer or select the link shown in Figure 1.
- Select the source WestGrid endpoint in the "Endpoint" field. You may browse the drop-down list or type the name into the Endpoint field to find the desired endpoint. All WestGrid resources (and other Compute Canada sites) are listed under "computecanada#".  
- You will be asked to click a link which will redirect you to a WestGrid-hosted web page, where you can enter your WestGrid username and password. You will then be redirected back to Globus and your endpoint will be activated.
- Once the endpoint is activated you may browse and select the files/directories you wish to transfer.

