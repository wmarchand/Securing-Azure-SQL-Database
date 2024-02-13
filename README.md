<h1>Securing Azure SQL Database</h1>

<h2>Description</h2>
In this project you will create a virtual network in Azure and utilize it to limit network access to your Azure SQL Database. You will create database users and roles to easily manage permissions in your database and enable auditing and system-versioning to monitor data changes over time. Besides implementing security and auditing features, you will define a backup policy for point-in-time and long-term retention backups. By completing this project, you will understand how to secure your database and restore your data in case of an accident or a security threat. 

<h2>Project Tasks</h2>

1) Setting up your environment
2) Limiting network access to your database
3) Creating a dedicated database user for your application
4) Azure SQL Database Auditing and Temporal Tables
5) Defining a backup policy for you Azure SQL Database

<h2>Pre-Project Set-Up</h2>
 - Sign up for a free Azure Account or use an exsisting account <br/>
 - Login to the Azure Portal
 <br />
 <br />
 <p align="center">
 Login to portal.azure.com: <br/>
 <img src="https://i.imgur.com/TUzFP8L.png"/>

<h2>Program walk-through:</h2>

<h3> 1) Setting up your environment</h3>

<br />
<p align="center">
First thing we need to do to set up our environment is to create a Resource Group. I named mine RG-USE-SecureDB. <br/>
<img src=""/>
<br />
<br />
Next we need to make a Virtual Network. I named mine VNET-USE-SecureDB.  <br/>
<img src=""/>
<br />
<br />
We do not need a lot of IP addresses, for my address space I used 10.2.0.0/24. I also added a Subnet with the same range and named it SNET-USE-SecureDB.  <br/>
<img src=""/>
<br />
<br />
We will now create a VM for our environment. I named mine VM-USE-SecureDB. Select Noinfrastructure redundancy required, choose the default Ubuntu Server (make sure it is LTS), and the standard B1s will do.  <br/>
<img src=""/>
<br />
<br />
We are going to be using SSH public key as our authentication type, choose your username and key pair name, also ensure that port 22 is allowed because we are planning on connecting to our VM through SSH.  <br/>
<img src=""/>
<br />
<br />
Change the OS disk type to Standard HDD.   <br/>
<img src=""/>
<br />
<br />
Finally, we need to create a SQL Database. Choose a name, I chose DB-USE-SecureDB. Click on Create new under Server.  <br/>
<img src=""/>
<br />
<br />
Choose the server name, mine is sql-srv-use. For the authentication method choose Use SQL authentication. Make sure you remember the username and password you set up.  <br/>
<img src=""/>
<br />
<br />
Click on configure database and choose Basic(For less demanding workloads) under the DTU-based purchasing model. <br/>
<img src=""/>
<br />
<br />
Scroll to the bottom and choose Locally-redundant backup storage.  <br/>
<img src=""/>
<br />
<br />
Under the Networking tab, select public endpoint. This is not a secure setting but we will fix that later.  <br/>
<img src=""/>
<br />
<br />
In the additional setting tab under Use existing data, choose Sample. Then Review + create.  <br/>
<img src=""/>
<br />
<br />

<h3> 2) Limiting network access to your database</h3>



<!--
  <br/>
<img src=""/>
<br />
<br />
