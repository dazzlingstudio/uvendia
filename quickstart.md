# Quick start
## Installation
Go to ``Umbraco > Packages`` and search for **Uvendia E-commerce** and install it.

### Database
Please run the SQL script ``uvendia.sql`` located at ``\umbraco\uvendia\content\sql\uvendia.sql`` after installation on your develop SQL Server. This script will generate all the tables, table indexes, table schema, stored procedures and triggers you need for **Uvendia**. You can also create a separate database if you want to, just make sure your connection string has the name ``unvendiaDbDSN``.

#### SQLCMD mode
Make sure SQLCMD mode is enabled before running the sql script. [Here](https://www.sqlshack.com/use-sqlcmd-commands-ssms-query-editor/) you can find how to enable it.

### Connection string
By ``default`` **Uvendia** will always take the **Umbraco** connection string named ``umbracoDbDSN``. But in case you want your **Uvendia** database table to be created on a separate database, you can configured another connection string with the name ``unvendiaDbDSN``.

## Assign Access
To assign access to the current user, please sign in into **Umbraco CMS** go to ``Users > Groups > [Select your group] > Sections > Add > Uvendia``.

![Assign Assess](/images/assign-access-uvendia.jpg)

## Cloudinary
Make sure you have an active account on [Cloudinary](/settings/cloudinary.md). Make sure the ``Web.config`` has the right [settings](/settings/cloudinary.md) configured.

## Settings
Before starting creating your assets, make sure you have all your settings configured. Take a look at the ``Settings`` sections.

## Demo
To see **Uvendia** in action as webshop go to [demo.snuffo.com](https://demo.snuffo.com). \
For **Uvendia** as asset management system installed into **Umbraco** go to: [demo.snuffo.com/umbraco](https://demo.snuffo.com/umbraco). 
```
Username: info@snuffo.com
Password: Y(I=%&aG.+
```

## Source code of the demo
To download the demo source code, go to [github.com/dazzlingstudio/snuffo](https://github.com/dazzlingstudio/snuffo)

## Licensing
**Uvendia** is actually free to use locally, but in case you are satisfied and want to use it in production, go to [Uvendia.com](https://www.uvendia.com) to purchase your license.

## Support
For details about support, please go to [Uvendia.com](https://www.uvendia.com/support)