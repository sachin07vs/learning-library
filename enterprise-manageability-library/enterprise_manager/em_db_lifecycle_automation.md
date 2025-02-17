![](media/rdwd-emheader.png)

Introduction
============

>   The objective of this lab is to become familiar with Oracle Enterprise
>   Manager Cloud Control 13c’s Database Lifecycle Management capabilities and
>   ability to move to the cloud using Oracle Multitenant Database. You will
>   learn how to request a pluggable database for testing purposes and perform
>   lifecycle operations like clone, unplug etc. You will set up a private cloud
>   for PDB’s, provision, resize and deleting a PDB using a self-service option.

>   Applicable User Roles in the Organization

![](media/ca612c296dce62109ae33de2f81110a7.jpg)

=============================================================

### Contents

**Lab Activity 1:** Requesting a Pluggable Database
    (PDB)

**Lab Activity 2:** Unplug a Pluggable Database and then Plug
    it Back In

**Lab Activity 3:** Creating Pluggable Database PDB Full
    Clone

**Lab Activity 4:** Compliance for PDB
    
**Lab Activity 5:** Use Self-service to request a PDB using
    PDBaaS (Private Cloud)

**Lab Activity 6:** Administrative Setup for
    PDBaaS (Private Cloud)
    





>   The estimated time to complete all the lab activites is approximately 60 minutes.

| **No** | **Feature**                                                                | **Approx. Time** | **Details**                                                                                                                                                                      | **Value proposition**                                                                                                                                                                                                                   |
|--------|----------------------------------------------------------------------------|------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1    | Requesting a Pluggable Database (PDB)                                      | 10min                     | Creation Pluggable database (PDB’s) within a CDB and run a post-script to lock/unlock accounts.                                                                                  | Create multiple PDB’s with few clicks while making sure they follow organization’s standards by using automated post-scripts.                                                                                                           |
| 2    | Un-Plug a Pluggable Database and then Plug it back (create from unplugged) | 10min                     | Un-plug a PDB and later Plug it back in a CDB when needed                                                                                                                        | Unplug a PDB when not needed and plug it back as per need hence maximizing resource utilization in your organization. Easily upgrade PDB’s with few clicks by moving from one container to another.                                                                                                                  |
| 3    | Creating Pluggable Database PDB Full Clone                                 | 5min                      | Create multiple copies (Clones) of a PDB to dev/test purpose                                                                                                                     | Create multiple PDB’s clones for Dev/test with few clicks while making sure they follow organization’s standards by using automated post- scripts.                                                                                      |
| 4    | Compliance for PDB                                                         | 10min                     | Apply a compliance standard on PDB and use corrective action to fix the violation                                                                                                | Make sure PDB’s comply with compliance standards and fix them with a click of a button of there is any anomaly.                                                                                                                         |
| 5    | Use Self- service to request a PDB using PDBaaS (Private Cloud)            | 10min                     | Request PDB pluggable database using Service Catalog. Resize the PDB and then Delete the PDB while preserving the contents.                                                      | Review self-service option to provision PDB, which only requires minimal inputs.                                                                                                                                                        |
| 6    | Administrative Setup for PDBaaS (Private Cloud)- Review only               | 10min                     | An overview of the administrative setup involved for PDBaaS which includes setting up a PaaS Infrastructure Zone, Pluggable Database Pool, Data Sources, Service Template, etc., | Setup private cloud using Enterprise Manager where admin can define resources and EM’s placement algorithm makes sure that resources are utilized to their best. It is complimented by metering, and show back/chargeback capabilities. |

>   

**Know your environment**
=========================

>   This is a self-sufficient environment with Enterprise Manager 13.3 as well
>   as all Database targets running on a single Virtual Machine.

| **OMS URL**          | https://\<public Ip address\>:7803/em                        |
|----------------------|--------------------------------------------------------------|
| **EM Credentials**   | Username: sysman Password: welcome1                          |
| **Database (CDB)**   | CDB186 (18.8)                                                |
| **DB Credentials**   | Name Credential as specified in use case or use sys/welcome1 |
| **Host Credentials** | Login as OPC user using your private key                     |
| **Startup Scripts**  | All scripts are in /home/oracle                              |

>   Self –Service User:

>   Username: CYRUS Password: welcome1

>   Sales (18.3)

>   Login to root if needed: sudo –s (from opc user)

>   Login to oracle if needed:

>   su – oracle (password : Commit12\#)

<br>**Lab Activity 1: Create Pluggable Oracle Database**
======================================================================



1.  Log into your Enterprise Manager VM using the IP provided on your cheat
    sheet. The Enterprise Manager credentials are “**sysman/welcome1**”.

2.  **Navigate** to the “Enterprise menu \> Provisioning and Patching \>
    Database provisioning”.

![](media/167e561726cc8d0a58d8b90a37274b06.jpg)

3.  In the Database Provisioning page, in the Related Links section of the left
    menu pane, **click** “**Provision Pluggable Databases**”

4.  In the Provision Pluggable Database Console, in the **Container Database**
    section, **select** the CDB (**CDB186 – 18.8 version**) within which you
    want to create new PDBs.

![](media/4a1835f78c064502ccac88138075133c.jpg)

5.  In the PDB Operations section, **select** Create Pluggable Databases ,
    **Click** Launch

![](media/2248640eabc0efa2fb32293ec07fb389.jpg)

6.  Use the named credentials (CDB186_SYS) for login

![](media/8741cbb813d375a296f8344f4beaeb7e.jpg)

![](media/9be6823423a692b7e1f0e240c10567c9.jpg)



7.  In the Source page of the Create Pluggable Database Wizard, in the Source Type section, **select** Create a new PDB . **Select** Named credentials “ORACLE”In the Identification page, **enter** a unique name for the PDB you are
    creating (your initial_pdb). **Optionally**, **select** check box to “create
    multiple DBs” and put **2** as number of copies.

8.  In the PDB Administrator section, **enter** the credentials of the admin
    user account you need to create for administering the PDB. **UserName**: pdbadmin **Password**: welcome1 **Click** Next.



![](media/7442f8d5bf4704af57849ae9741f5a36.jpg)

9.  For storage option, **select** “Use Common Location for PDB Datafiles” and
    leave defaults as-is.

![](media/e42b8bce3bdaac0c78fccbe24f1ede48.jpg)

10. Optionally, you may also want to select a post-script, which will run post
creation of PDB. Choose “Select from software library” and then search for
“**unlock**” and select unlock.sql (Or you can upload a SQL file from your
system).

![](media/7d3fcabc8fe5f6f80fe20e55bb28655d.jpg)

11.  In the Schedule page, **select** immediately check box next to Start.
    **Click** Next**.**

12.  In the Review page, review the details you have provided for the deployment
    procedure. If you are satisfied with the details, click Submit. You can now
    click on View Execution Details link to see details.

![](media/d12c1a1d5e3c3f394248da7d12813b6b.jpg)

13.  In the Procedure Activity page, view the status of the procedure. Click the Status link for each step to view the details of the execution of each step.


 
![](media/3657eb9bb536b26d163c148e40a99332.jpg)

14. Once the procedure is completed (takes about 3-5 mins), you can **Navigate to
Targets \> Databases, Click on CDB186** and you will see the newly created PDB

![](media/657ef309d7087942b8d871256a359050.jpg)

<br>**Lab Activity 2: Unplug/Plug an Exisiting Pluggable Database (PDB)**
======================================================================


1.  **Navigate** to the “Enterprise menu \> Provisioning and Patching \>
    Database provisioning”.

![](media/167e561726cc8d0a58d8b90a37274b06.jpg)

2.  In the Database Provisioning page, in the Related Links section of the left
    menu pane, **click** “**Provision Pluggable Databases**”

![](media/33b77cf547caf09fe9c2d56b23fbaf43.jpg)

3.  In the Provision Pluggable Database Console, in the Container Database
    section, **select** the CDB (**CDB186**) within which you want to create new
    PDBs.

![](media/4a1835f78c064502ccac88138075133c.jpg)

4.  In the PDB Operations section, **select Unplug** Pluggable Databases ,
    **Click** Launch

![](media/b727e1673cfa38c85130ef6e2365055d.jpg)

5.  In the **Select** PDB page of the Unplug Pluggable Database Wizard, in the
    Select Pluggable Database section, select the PDB you want to unplug. Also
    **Select** Named credentials “ORACLE”

![](media/39102476b5e5915a1491e28525af88f5.jpg)

6.  In the Destination page, select the type of PDB template you want to
    generate for unplugging the PDB, and the location where you want to store
    it. The PDB template consists of all datafiles as well as the metadata XML
    file. **Select** radio button for software library. **Select** Generate PDB archive. **Enter** /tmp in location under Temporary working directory





![](media/4ad828f403bf702b7318f718ad98f117.jpg)

7.  In the Schedule page, **Select** immediately check box next to Start. **Click Next.** In the Review page, review the details you have provided for the deployment
    procedure. If you are satisfied with the details, click Submit. In the Procedure Activity page, view the status of the procedure.




![](media/bdbafe949b2bc880e2a09b82f9edaf8a.jpg)

8.  You can **Navigate to Targets \> Databases,** Click on CDB186 and you will
    see the PDB you unplugged is no longer in the list.




9.  Let us continue to next steps and plug the same PDB back into the container database. Navigate to the “Enterprise menu \> Provisioning and Patching \> Database
    provisioning”.

![](media/167e561726cc8d0a58d8b90a37274b06.jpg)

10. In the Database Provisioning page, in the Related Links section of the left
    menu pane, **click** Provision Pluggable Databases

![](media/33b77cf547caf09fe9c2d56b23fbaf43.jpg)

11. In the Provision Pluggable Database Console, in the Container Database
    section, **select** the CDB (**CDB186**) within which you want to create new
    PDBs.

![](media/4a1835f78c064502ccac88138075133c.jpg)

12. In the PDB Operations section, **select** Create Pluggable Databases ,
    **Click** Launch

![](media/2248640eabc0efa2fb32293ec07fb389.jpg)

13. In the Source page of the Create Pluggable Database Wizard, in the Source
    Type section, select **Plug an unplugged PDB**. **Select** Named credentials
    “ORACLE”

![](media/5427807b6e4c677bd991497cfc5468ce.jpg)

14. In the Identification page, enter a unique name for the PDB you are plugging
    in. **Select** Create As Clone to ensure that Oracle Database generates unique PDB DBID, GUID, and other identifiers expected for the new PDB. **Enter** PDB name like “clone_pdb”.





![](media/2ac79b220d664b868c62e4529791e187.jpg)

**Note**: We will keep pdbadmin as a default admin. So, don’t select
    anything in this section.

17. On the Identification page, in the PDB Template Location section: **Select** “Software Library” radio
    button. **Click** on the magnifier icon placed on Location text box. **Select** the Name which you created During Unplug **Click** Next

>   

![](media/dad1846d73cd9ca339bab04718e09816.jpg)

18.  **Select** “Use Common Location for PDB Datafiles” and use **/tmp** as
    temporary working directory.

![](media/a6353f812935eeb6148a79693ae0c4fd.jpg)

21.  In the Schedule page, **select** immediately check box next to Start.
    **Click** Next.

22.  In the review page, review the details you have provided for the deployment
    procedure. If you are satisfied with the details, **click** Submit. You can
    now click on View Execution Details link to see details.

23.  In the Procedure Activity page, view the status of the procedure.

24. Optionally **Click** the status link for each step to view the details of the
execution of each step. Once the procedure is completed, you can **Navigate to
Targets \> Databases,** Click on CDB186 and you will see the newly created PDB



Note: You do not have to wait until the steps complete and move on to the next section.


<br>**Lab Activity 3: Clone an Exsiting Pluggable Database (PDB)**
======================================================================



1.  **Navigate** to the “Enterprise menu \> Provisioning and Patching \>
    Database provisioning”.

![](media/167e561726cc8d0a58d8b90a37274b06.jpg)

2.  In the Database Provisioning page, in the Related Links section of the left
    menu pane, **click** Provision Pluggable Databases

![](media/33b77cf547caf09fe9c2d56b23fbaf43.jpg)

3.  In the Provision Pluggable Database Console, in the Container Database
    section, **select** the CDB (**CDB186**) within which you want to create new
    PDBs.

![](media/4a1835f78c064502ccac88138075133c.jpg)

4.  In the PDB Operations section, **select** Create Pluggable Databases ,
    **Click** Launch

![](media/2248640eabc0efa2fb32293ec07fb389.jpg)

5.  **Select** clone PDB and select source as CDB186 (if you choose any other
    CDB, this operation might fail). Please keep Database link box empty. Select named credentials “ORACLE”, **Click** Next.



![](media/472126037592bdeca5eaa6027ebb57a3.jpg)

6.  **Enter** new PDB name

![](media/4a4164d7ee405fed16dc5a0aeefe430f.jpg)

7.  **Select** “Use Common Location for PDB Datafiles” in the Source page of the
    Create Pluggable Database Wizard, please enter **/tmp** in temporary working
    directory. Optionally, you can select the postscript as we did in the creation flow.
**Click** Next



![](media/ff556eb15570c55dfd477361c20051d6.jpg)

8.  When the see the Schedule page, just **select** the immediately check box next to Start. Then **Click** Next.

![](media/dblmschedulepage.jpg)
    


9.  After the Review page appears, and you have confirmed the information is correct for your deployment, click Submit. You can now
    click on View Execution Details link to see details and on the Procedure Activity page see the status of the procedure.
    


10.  Once the procedure is completed,  **Navigate** to Targets then
**Databases**, then **Click** on CDB186 and you will see the newly created PDB



<br>**Lab Activity 4: Compliance Management for PDB**
======================================================================


>   Now database administrator applies a Corporate Standard on the newly created
>   PDB database, which results in a “Violation”. Then, the DBA fixes the issue
>   using corrective actions. Let us examine how a DBA applies the fixes in the
>   following steps.

**Click** ![](media/2e18c410493be6ec0b9352b94c0ceb9c.png) then **Click** Compliance, then **Click** Library to get started

![](media/dblmcompliancelibrary.png) 

1.  **Select** the Compliance Standards tab,  then Choose the row “Corporate Database Standard” then **Click** the OK button

![](media/8ed5400adb044b81194db800cfd4c953.jpg)


2.  In the Save Association box, **Click** the Yes button

![](media/0ccc894ff6c91bdd0aa1b7e5f78fbe6e.png)

3. Then upon the Information prompt, **Click** the OK button

![](media/a01dffb956af685a866f02e68eff72b1.png)



4.  You need to refresh PDB statistics to see notifications. To refresh: 

    a.  **Click** the target icon, then **Click** Databases, then **Click** View, then **Click** Exapand All


    b.  Then **Right Click** on PDB, then **Click** Oracle Database, then **Click**  Configuration, then **Click** Latest. 
>   **Click** the Refresh icon on the page (it will take few minutes for refresh to complete)

5.  Now **Click** ![](media/2e18c410493be6ec0b9352b94c0ceb9c.png) then **Click** Compliance, then **Click** Results



![](media/1317deb228d80211d9e6a2edf2cbba9e.png)

6. Click Corporate Database Standard under Compliance Standards

![](media/4fd761f917fd5b2374e852575b2fe99f.jpg)


7. And you  will see the following screen 

![](media/1376bfeae918518dbfd16d32ffc67b72.jpg)





8.  Click Violations link and  click on one of the Open Cursor Setting lines on the left under the Corporate Database Standard heading (red x).

![](media/e48f5a64f52812e23a631e0f3f270371.jpg)

9.  You will see open cursors notification. Scroll down as needed then **Click** on the link “Submit from Library” link under the Corrective Actions heading. 

![](media/19317a4da691bc2a1049ca7923414db3.png)

10. From the Corrective Actions popup box, Select the “FIX OPEN CURSOR” corrective action.

![](media/61ea7b2393701bf4ce48bd301a67b332.jpg)

11. Then review/enter the Named Credentials for the database and host and **Click** the Submit button

    a.  For the database named credentials use: OEM_SYS (scroll down after Database Credentials to see Host Credentials

    b.  For the host credentials use: ORACLE_HOST

![](media/6ccf17bb69cbc79dae30f95bc508f640.jpg)

13.  You will then see the popup as shown below. **Click** on the link “Click here to view the execution details”

![](media/21e5a02e32296dd7dea196a7edfd29ac.jpg)

>    The job will take about a minute to complete. Click on refresh icon if the job did not complete. You will see the status change to Succeeded

![](media/3be714a84eeca17c22b2c786688b567a.jpg)


14. Once the status changes to Succeeded, **Click** Databases **Click** View
    **Click** Expand All **Click** on Your PDB that you choose in the earlier step.

15. Under Administration drop down **Click** Initialization Parameters, then Scroll down and you will see the “open_cursors” initialization parameter set
    to 400 as shown. 


![](media/6b842b0948b11c52c1d56d2f9cdf1088.jpg)

>   Now that you have gone through PDB life cycle operations, we
>   will switch focus and cover the use case of building a private cloud using
>   Enterprise Manager and how to quickly provision (with
>   minimal inputs) and manage PDBs using PDB-as-a-service (PDBaaS).

<br>**Lab Activity 5: Self-Service to Request PDB Using PDBaaS**
======================================================================



With the Self-Service Portal, cloud users can request an  Pluggable Database through a simple process, monitor resource consumptions, and manage the
pluggable database through an intuitive graphical user interface. Expiry time is provided while requesting the PDB instance and PDB is automatically deleted based on the expiry time.



1.  Login into Enterprise Manager as a Self-Service User. Self-Service User
    credentials are: **cyrus/welcome1**


2.  By default, you'll see the Database Cloud Self Service Portal landing page
    as shown below.

![](media/2d9dd5550b4774b590ccb4b1815ac70d.jpg)

3. **Click** the “Create Instance” button and then **Click** on Select icon for “**Provision New Empty Pluggable Database**”

![](media/ee694403e4c718e224a01ae91dbc88fd.jpg)

**Note: There are two service templates pertaining to Pluggable Database**

-   **Provision New Empty Pluggable Database**

    -   This template enables users to create a new pluggable database in a
        container database configured by DBA

-   **Provision Pluggable Database with Data**

    -   This template enables users to create a new pluggable database with data from non-container database.
        


4.  In the “**Pluggable Database Configuration**” section, enter Service and SID details :

      Name: **YOUR INITIALS_PDB2** (e.g. AS_PDB2)

      Database Service Name **: SERVICE_YOUR INITIALS_PDB2 (e.g. SERVICE_AS_PDB2)**

      Workload Size: Choose **Small**

![](media/fd8fe73465009dbd65e2231503481e40.jpg)

5.  Enter Credentials details in the “**Pluggable Database Administrator
    Account**”

      Administrator Name: **PDBADMIN**

      Password: **welcome1**

    Confirm Password: **welcome1**

     Tablespaces: **Accept default**

![](media/181bed80a9978ed3e02c050838749f2b.jpg)

6.  Instance Details, keep all defaults as they are. The Properties Page has the properties for the instance. The Self-Service Administrator has configured
        this as a optional step. However, properties can help users locate an instance more quickly. So Enter

        Contact: **CYRUS**

        Lifecycle Status: **Test**

![](media/f5f29e12efaaf8a1fce318e871d9009d.jpg)

7.  Instance Duration - For Instance Duration Start: Accept the default (Immediately). For Duration: Specify 4 hours from the
        current time by selecting the “Until” radio button, changing to current
        date and specify time to be 4 hours from the current time



![](media/3035739cd46353882939fd894197f2ed.jpg)

8.  Click on Submit button

>   What do these options represent? In most cases the PDBaaS options are
>   self-explanatory. The self-service user should be able to provision a PDB by entering minimal information. Fields with an ‘\*’ represent mandatory input fields. Please refer to the
>   table listed below for a description of each option:




| **Field**                   | **Description**                                                                                                                                                                                                                                                                                    |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Request Name                | By default, it is the Self-Service User Requestor name with timestamp. This field can be modified                                                                                                                                                                                                  |
| Zone                        | The Zone is a PaaS Zone that represents hosts/vm, where the PDB database will be deployed for this request. The zones are configured by the administrator. Self-service user need not know the host or platform details.                                                                           |
| PDB Name                    | Required input. PDB database with user defined will be created for the container database                                                                                                                                                                                                          |
| Database Service Name       | The user defined prefix for the database service or alias for this self-service PDB. The rest of the service name will be system generated and will be associated with a database resource management plan.                                                                                        |
| Workload Size               | The resources allocated to the Database Service. The database resource management plan is derived from this option. You can configure multiple workload sizes. Each service template will contain unique workload sizes. This typically depends on the roles assigned to self-service user.        |
| Schedule Request            | Self-service user has the ability to create a PDB database immediately or choose to create at a later time. In this lab exercise, the administrator has defined a policy, so a self- service user has to specify time duration. The PDB database will be automatically deleted after the duration. |
| Administrator Name/Password | A database user with required administrative privileges will be created on the provisioned PDB. A self-service user will be able to administer the PDB database by logging in as this database user.                                                                                               |

9.  Once you submit a request, you will be redirected back to the “**Database
    Cloud Services**” Page. Your PDB creation request has been submitted to
    Enterprise Manager for execution. Under “**Requests**” region, you should
    see 2 requests: “**Create**” and “**Delete**” request

![](media/0d01a3a45ebb7f97fcc8752d52241b9d.jpg)

10. At this point, provisioning engine has received a request to create a PDB
    based on the service template and input provided by self-service user. You will also notice the delete operation is scheduled for future (not
    started yet) time. Click on the **hourglass** icon under Status column for
    the Create Pluggable Database step. You will see details of request.

11.  It will perform the following actions:

>   
        Create database roles and PDB

        Create a resource plan based on the workload size

        Create and register the database

        The request should take less than 10 minutes to complete. Click on refresh
        icon or as an alternative set Refresh to 30 seconds. The success status
        indicates that PDB database was successfully created. The new PDB database 
        should be visible under Database Cloud Services page.

![](media/3fc668c3d45cc0a1a7dc3c3f7233bfe6.jpg)

12. Click on Close button. You will see the following under Requests section.

![](media/9bd785e399889d2a53d9e7284bf6c329.jpg)

13. Click on the Home Icon. You will see new PDB instance.

![](media/ee3e8bccf25b8a836bea2f9a3a487cb7.jpg)

Note
----

Following widgets are shown on the Database Cloud Services landing Page

    **Instances** show the number and status (Up/Down) of the DB/PDB Instances
    provisioned by the self-service user.

    **Expiry**, shows the expiration summary of DB/PDB Instances.

    **Usage**, resource usage status for the Self-Service user, status of the
    resource consumption for this user.

    **Memory**, current memory consumption against the Quota for this user.

    **Storage**, current storage consumption against the Quota for this user.

14. Click on the name of the PDB. You can use the connection details to connect to the PDB using SQL tools.


![](media/9ca31e90c86263e6cddde14da1c6954f.jpg)

15. Click on **Resize** button to resize a PDB instance.

![](media/20537907e3a274a9df16e7c54f73713f.jpg)

>   Resize allows you to resize your instance to other available resource sizes.
>   We have 2 resource sizes available for Service Template. Both are displayed.
>   Current size of PDB instance is Small, you can now resize it to large.

![](media/cc03cc86d7e3d8146a3d799b52583a83.jpg)

16. One you click on **Resize**, a job will be submitted to resize instance. In
few minutes instance resize is completed. Expand **Resource Usage** section on PDB Home page. This shows now new resource usage limits.



>   
![](media/64a8954df11d2e688a930fd92ae38cd8.jpg)

17.  Next delete the database Instance: Go to the Database Cloud Services Home page by clicking on **Database
        Cloud Service Portal link**



![](media/a24b112c579e1df59bb4919a0bbe2b67.jpg)

18. Click on the action menu for new PDB and delete this instance.

![](media/877bc45ab2f0ab8acd7ea6507baee575.jpg)

19. While deleting instance you can preserve a backup of the instance and create a new instance using this backup. To store backup of this instance, select check-box: **Preserve a backup of this instance**

  
![](media/2840b2e0869edc22af3245e98dba13eb.jpg)

20. Click OK. You will see confirmation to delete the instance.

![](media/2b44dd4c41f594cddd9adc74dd193297.jpg)

<br>**Lab Activity 6: Administrative setup for PDB-as-a-Service (Private Cloud)**
======================================================================


Previous exercises demonstrated the process of requesting PDBs using
available service templates as performed by a Self-Service user. In this section,
we will see the Administrative setup for PDBaaS.

Login to the EM Console as super administrator **sysman/welcome1**

PaaS Infrastructure Zone
------------------------

1. On the EM Console, go to Setup -\> Cloud -\> Database.

![](media/edfbce40d3abb0f21705992cc042c3ee.jpg)

2. Select **Pluggable Database** from the drop-down menu.

![](media/cf57fcbd4fe1570c40a1ee7f9b75dcec.jpg)

3. Then **Click** on **PaaS Infrastructure Zone** **Sales Infra Zone** is the zone where PDBs were provisioned in the
previous sections. **Click** on name of the zone.


![](media/8ed6c692f382172bbc9f6e2b90179f9e.jpg)

4. You are taken to the Zone Home page; you can see all the details of a Zone
such as the host members of this zone. You can explore more about the zone
on this page.

![](media/b3ddc4d5e436d1e6dec7eb0ed795f0b7.jpg)

Pluggable Database Pool
-----------------------

5. On the EM Console, go to **Setup**, then **Cloud**, then **Database**. Select **Pluggable Database** from the drop-down menu. And then click on **Pluggable Database Pool**’.

>   A Pluggable Database Pool consists of a set of Container Databases on which
>   PDBs will be provisioned.

![](media/b49f455842d0fb11dd7de44fcaccfe26.jpg)

6. Click on name of the pool to see more details.

![](media/5fa7e9b6bb3648c664e4afc7aeac5670.jpg)

7. Scroll down to see details of Members and Service Templates.

![](media/243ed347412f16a2159b2184c2dacdf7.jpg)

Data Sources
------------

8. On the EM Console, go to **Setup**, then **Cloud**, then **Database**. Select Pluggable Database from the drop-down menu. And then click on **Data Sources** observe that the profile is based on Schema Export(s). This Data Profile was used for provisioning a PDB with data.

![](media/d834209bf1c6a238679ae419098ee0f3.jpg)

9. Select the row with profile to see more details.

![](media/532db10bbaab85fcdd83f245bd317a6b.jpg)

Service Templates
-----------------

10. On the EM Console, go to **Setup**, then **Cloud**, then **Database**. Select Pluggable Database from the drop-down menu. And then click on **Service Templates from you left menu.**

![](media/47baba2a1e7567bfb0b5f89429a7831d.jpg)

>   There are two service templates pertaining to Pluggable Database

-   **Provision New Empty Pluggable Database**

    -   This template enables the user to create a a new pluggable database in a
        container database configured by DBA

-   **Provision Pluggable Database with Data**

    -   This template enables user to create a new pluggable database with data
        from a non-container database.

11. Click on name of any template to explore more details.

![](media/a0efb63a12d01e1254593656765ec52a.jpg)

That concludes this lab. 

>   [Return back to top menu listing all available labs](../readme.md)