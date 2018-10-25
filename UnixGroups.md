# File Sharing
## Using UNIX groups to control file access
### Introduction

This page shows how to request and use UNIX groups to facilitate sharing of files among researchers on WestGrid systems.

As explained in most introductory tutorials, each UNIX (or Linux) file or directory is owned by an individual user and also by a group (which may be comprised of several users). Permission to access files and directories can be restricted to just the individual owning the file, to the group that owns the file, or, access can be unrestricted.

By default, each WestGrid account (username) is set up with an associated UNIX group containing just that single username.  So, even if you have set permission for your UNIX group to access files, they are still not being shared with anyone else.  You can override the default by using the chmod command to set unrestricted read access to your files. However, if you need more specific control over access, you can ask for WestGrid to create a special UNIX group containing the usernames of other researchers with whom you want to share data.
### Requesting a UNIX group

If you do wish to share files using UNIX group permissions, mail WestGrid support to ask that a new UNIX group be created for you.  Include a list of the users who should be added to that group.  One user should be designated as the authority for the group.  If a request to join the group is made from someone else, WestGrid will ask the designated authority for permission to add the new researcher to the group. The group name must be of the format wg-xxxxx where xxxxx represents up to five characters. Please indicate your preference for a group name in your email.

The group will be set up on all the WestGrid systems. This may take a day or two to set up . You will get an email whenever you are added or removed from a WestGrid UNIX group.
### Using a UNIX group to facilitate file sharing

The directory you wish to share should be owned by the group and permitted to the group. For example:

<code> chgrp -R wg-group <dir> </code>

<code> chmod g+s <dir> </code> 

Note you must ensure that there is access to parent directories as well.

A directory and all the files in it can be permitted to the group as follows.  Use

<code> chmod -R g+rX /scratch/dirname </code>

to set access for the /scratch/dirname directory and all its subdirectories. Note the uppercase X in the command. This will set x permissions on the subdirectories (needed for others to list the directories) as well as regular execute permission on executable files.

If you want the to allow other members to not only read files in the shared directory <dir>, but also permit write access to allow other members to create and change files in that directory, then all members in the group must add a line

<code> umask 007 </code>

to the .bashrc or .cshrc file in their respective home directories. Furthermore, you must add write permission to the shared directory itself:

<code> chmod -R g+rwX <dir> </code>

which would allow read and write access to the directory <dir> and all its files and subdirectories.

Note: For orcinus, all members of wg-group who are not primary owners of shared directories have to issue 'newgrp  wg-group' command before accessing the shared directory.

