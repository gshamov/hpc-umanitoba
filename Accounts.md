= User Accounts and Access to the system

WestGrid and Compute Canada facilities are designated for Canadian researchers or those collaborating on Canadian research projects. In general, any academic researcher from a Canadian research institution with significant high performance computing requirements to support his or her research may apply for an account. 
Any Compute Canada user can access modest quantities of compute, storage and cloud resources as soon as they register with the Compute Canada DataBase (CCDB). This Rapid Access Service allows users to start working right away. Many research groups can meet their all their resource request needs through using the Rapid Access method. Users requiring larger resource quantities can apply to one of Compute Canada's annual Resource Allocation Competitions.

== Eligibility of Conditions of Use
=== Criteria

WestGrid facilities are designated for Canadian researchers or those collaborating on Canadian research projects. In general, any academic researcher from a Canadian research institution with significant high performance computing requirements to support his or her research may apply for an account on WestGrid.
Faculty members and senior researchers at a Canadian university or research facility are eligible once registered in the CCDB. Graduate Students and Postdoctoral Fellows are eligible but must be sponsored by a faculty member, who must register in the CCDB first.

=== Permitted Uses

TODO: Westgrid is irrelevant

== Conditions of Use
=== Responsible Use of Westgrid facilities
A user of WestGrid facilities must agree to abide by the following conditions:

- The WestGrid facilities are governed by rules set down by the WestGrid Executive Committee and/or the WestGrid Chief Technology Officer. All users must agree to abide by these rules.
- A user is responsible for his or her account and all activities that are performed using his or her account.
- A user must not make his or her account available to any other user.
- Accounts and allocations are to be used exclusively for the purposes and project(s) for which they have been approved.
- WestGrid resources are provided for support of research and may not be used for instructional or administrative purposes.
- Users will be fair and considerate in their use of WestGrid resources.
- When requested, users must provide data that is required by WestGrid for purposes of reporting to the WestGrid funding agencies. This data must be provided in a timely fashion.

Failure to follow these directives may result in users and/or projects losing access to the WestGrid facilities. WestGrid reserves the right to take whatever actions are necessary to identify and resolve suspected abuse of the facilities. For cases not covered by this Conditions of Use statement, the computing policies in effect at the user's home institution shall apply.
=== Data Storage Policy

This page details WestGrid's policies around storage and management of user data.
==== Appropriate Use
All data stored on WestGrid systems must be directly related to a research project described in the user's WestGrid profile. Information about research projects is provided by the user during the account application process and can be updated by sending email to support@westgrid.ca. For example, it is appropriate to backup research data to WestGrid systems, but it is not appropriate to backup an entire machine or desktop. If there is any doubt about what is or is not permitted, please contact support@westgrid.ca.
==== Allocations
Researchers or projects with very large storage requirements must get prior approval from the WestGrid Resource Allocation Committe (RAC) or the Compute Canada National Resource Allocation Committee (NRAC).  See the Resource Allocations page for details. Requests for more than 2 TB in a volume that is backed up to tape or 5 TB in a volume that is not backed up must be directed to support@westgrid.ca. An application to the RAC or NRAC may be required.
==== Quotas
File system usage is monitored by the systems, and users are kept from exceeding set limits.  Quotas can be set on number of files and on total storage used. There is a "soft" quota and a "hard" quota. Users are expected to keep their usage below the soft quota limit, however they are allowed to exceed the soft quota limit for a short period of time.  Users are not allowed to exceed their hard quota limits. 
If a user or project needs more storage on an ongoing basis than is allowed by the quota limits, a request can be made for a higher quota. Any requests for increase in quota at storage facilities should be made to support@westgrid.ca and should include a brief description of why the increase in quota is required. Requests for small storage quota increases can be decided by the WestGrid site leads. Large storage requests must be approved by WestGrid RAC or NRAC, as stated above.
==== Backups
A backup is defined as a file stored on tape that matches a file on disk. The backup will be maintained for the duration of the WestGrid project on tape or until the file on disk is deleted.  After the file is deleted, the backup will be deleted off tape after a retention period (often in the range of a few to several weeks). Backups are intended to reduce the risk from disk crashes and user errors such as accidental deletion of files. Some data can be recreated, some cannot.
Some filesystems or volumes are backed up and some are not. The number of copies of files, the length of time they are kept, and other details vary. See the site-specific web pages for details.   Since keeping backups adds to the cost of data storage, users should think carefully about what files are stored in these volumes. The most expensive backup systems will require RAC approval.
Archives
An archive is a file stored on tape that is being kept for possible future use. If an archive is created from a file that resides on disk on a WestGrid system, it is expected that that file will be deleted from the disk after archiving. If an archive is created from a file on a non-WestGrid system, no assumptions are made about whether the file has been removed or not at the source.
An archive is stored for a specified period of time, selected at the time of creation (typically in the range of years, e.g. until the end of the WestGrid project unless the archive is needed only for a shorter period of time). After that period of time, the archive is deleted. There are no long-term/ongoing plans to operate or keep archive tapes forever. For example, the WestGrid site at the UofS would attempt to keep archives past the termination of the WestGrid project on a best-efforts basis and depending on future operational funding.
The WestGrid project is funded by a series of grants, each approximately 5 years. There is no guarantee that WestGrid will continue past the current grant, just an expectation that it will. In the event that WestGrid is no longer able to archive your data following the completion of the project users will be given an opportunity to retrieve their data. Users must request that files be archived; users cannot do this themselves.

====Ownership of data
If there is disagreement between a project leader and a user about the ownership of a user's files, WestGrid will consult the legal policies of the project leader's home Institution as well as the Institution(s) hosting the equipment on which the data is stored.  In the past, it has been WestGrid's experience that the policies of the project leader's home Institution have been used to resolve such disagreements. WestGrid advises researchers to review the appropriate institutional policies regarding ownership of data and privacy.

==== Retention of data

All data will be deleted from a user’s directories once their WestGrid account has been retired (this occurs 90 days after the account has been deactivated).  See the User Accounts pages for more information about the deactivation process. Some data may remain on backup tapes for a period of time. Any recovery of the user's data after account retirement is strictly on a best-effort basis with no guarantee of success.

==== Data Retention Policy for Defunded Systems

- The policy for all systems which will be defunded is to notify users (via any/all of the following methods: newsletter, email, website, MOTD, user docs wiki) at least 90 days before the date data may be deleted. 
- Data deletion dates will be posted for all systems which will be defunded.
- It is the responsibility of the host institution to determine which user data will be deleted and then purge files as needed.
- It is the host institution’s responsibility to develop and communicate any future policies on system use/access, account management, data retention policies, etc. to users.

IMPORTANT: Please note that WestGrid will not retain any long term back-up copies of user data. Users should ensure they take the appropriate steps to comply with any data management requirements their institution or project may require.
==== Risks of Data Loss

WestGrid makes no guarantees that any file can be recovered, regardless of where a file is stored, even in backed up volumes. Accidents happen, whether caused by human error, hardware or software errors, natural disasters, or other. It is the user's responsibility that the data is protected against possible risks, as appropriate to the value of the data. Best efforts will be made to ensure reliability for all researcher data. WestGrid can give no guarantee regarding the security of data, although every effort is made to ensure data is not compromised.

