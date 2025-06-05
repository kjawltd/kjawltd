Introduction

This installation reference contains the information you’ll need to install the product successfully. Before you start the installation, make sure you have all the information and permissions you need. Work through the checklists to collect this information and then you'll be ready to start. 
Checklists

•	Read through these checklists, as they contain technical specifications and user permissions you'll need during the installation.
 
Architecture / Hardware

•	The product can be installed using one of several architectural models, you can choose the right one for you from the architecture guide.
•	Check your installation hardware uses a minimum XGB RAM and Y core CPU.
•	Check you have a separate product licence for each separate installation environment (e.g. installing on a development environment and a live environment will require 2 licenses). 
Data

Here’s a list of the data values you’ll need to enter during the installation.
•	Admin module username and password to create a product administrator account.
Note: The admin module username and password can't be recovered, so if they're lost or forgotten you'll need to re-start the installation.
•	Database password and port number - you can either choose to create a new instance during the installation, or use an existing instance. 
•	Database version – we test the product against the current version of the database and support all versions above vX.0. 
•	Server host name and port number - the machine and port to run the installation
•	SSL certificate – You’ll need a valid SSL certificate to enter the certificate type, URL, directory path and password (if it's required).
•	Licence key – You’ll find a valid licence key in your licence information.
Note on HTTP: The product can be installed using HTTP, but we do not advise this option for production environments as it leaves you vulnerable to security breaches. 

 
Installation - network

Technical specification required for installation on a networked server.
•	Target Server - x64 Windows Server machine running Windows Server (v2008 R2 and above).
•	Ports - 2 ports need to be left open – one for the database and one for communication between end user connection locations and the target server.
•	Firewall – a port for communication needs to be opened.
•	SSL Certificate – this should be stored on a drive accessible to the server.
•	Windows Server account with administrative privileges.
•	Permission to write to the C drive on the target server. 

Installation - stand-alone server

Technical specification required for installation on a stand-alone server.  

•	Target Server - x64 Windows Server Machine running Windows Server (Version 2008 R2 and above).
•	Target Server - ports X  and Y (database) to be unused.
•	DNS - Certificate issued for DNS to be used by the product.
•	Virtual Proxy to be set up according to instructions in configuration guide. 
•	Windows Server account with administrative privileges.
•	Permission to write to C drive on target server.

Next steps - installation

Once you've worked through all the checklist items, you can install the product using the installation guide. 



