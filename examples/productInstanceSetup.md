---
title: Product Instance Setup | Examples
weight: 3
---

## Product Instance Setup Guide

### Introduction

Before you start using the product, you'll need to set up and configure an instance to store your data and any changes you need to make as your requirements evolve. Instances are configured in the admin module installed with the product. 
You can integrate the product with several different data output types, and this guide shows you how to create an instance to integrate with an SQL database. You can find a full list of output types in the product home page. 

### Checklist 

Work through the checklist we’ve included here to make sure you have all the information and permissions you need.

- Product login / password used in the installation.
- Database name, username, password, host name, port number.
- Instance name and connection name (you’ll create those when setup is completed).
- Database table name.
 
### Adding an instance

The first action you’ll need to complete is adding an instance. 
•	Log in to the Admin module to open the dashboard. You’ll see the navigation menu on the left, and current instances listed in the top right panel (Figure 1).

<Screenshot>
Figure 1: Admin module dashboard

**Note**: If the setup was successful, the instance will be marked with a tick, while instances containing errors are marked with a cross.
- Click **Instances** in the navigation menu to open the instances homepage (Figure 2). 

<Screenshot>
Figure 2: Instances 

- Click **Add instance** to open the pop-up screen where you enter your data (Figure 3).

<Screenshot>
Figure 3: Add instance

- Select **SQL** as the instance type.
- Enter the instance **Name** you’d like to use.

**Important**: The name will be displayed in every place where the instance is used, so please keep this in mind when choosing it.
 
- Enter the database connection details in the **Settings** panel (Figure 4).

<Screenshot>
Figure 4: Settings
  
There are two ways to enter connection details. We've included a numbered reference to show you where the values should go, but you'll only need to use one. 

- Enter the values for the **Database**, **Username**, **Password**, **Host** and **Port** in the text fields (numbers 1 – 5 in Figure 4).
- Enter a **Connection URI** in the URI field (number 6).

**Note**: The username and password you enter here is for your database connection. You won't be able to use your Windows username or password.

- Click **Add instance** when you've entered the connection details. You should see the new instance created in the dashboard (Figure 5).
  
<Screenshot>
Figure 5: Instance created
  
**Note**: Before configuring your instance, check the tick is displayed beside the instance name.
 
### Configuring an instance

The next action to complete is configuring the instance, to connect up your data with your database.
- Click **Configurations** in the navigation menu to open the configurations homepage (Figure 6). You’ll see the list of configurations displayed on the page.

<Screenshot>
Figure 6: Configurations

- Click **Add configuration** to open the popup screen (Figure 7).
**Note**: Your configuration id is generated automatically, so the ID field will already be populated.
  
<Screenshot>
Figure 7: Add configuration

- Enter a configuration **Name**.
- Select **SQL** as a configuration Type.
- Select the **Connection** name from the dropdown list.
- Select the database **Table** name.
- Click **Add configuration** to save your details. You’ll see the new configuration listed on the homepage.

### Next steps/Further reading

Now you can use the configuration to make data updates and have the data stored in your database. You can find full instructions on working with data in the product user guide.


