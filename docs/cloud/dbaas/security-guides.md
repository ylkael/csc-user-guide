# Security guideliens for DBaaS

## Firewalls
All database instances have their own firewalls. Users are responsible for making sure that the firewall rules are strict. The firewall rules should only be open to does IP-address that are absolutely needed. Relaxed firewall rules are probably the biggest security risks and you need to take it seriously. Even if you don't have any "secret" data in your database you are not allowed to have it open to the world. If you want to share your data you should do it through a proxy or other services that might use the database on the backend. An open database port on the internet is very easy way to attract hackers. 

## Authentication

Internal Beta: You can authenticate to DBaaS with your csc-customer account and password. 
Production: You can log in to the DBaaS service with a lot of different authentication methods as long as you have a csc-account [Create user a new user account](./../accounts/how-to-create-new-user-account.md) and belong to project that have applied for DBaaS access.

From the web interface you can create applicaiton credentials if you like to automate your database manage from another applciaiton.

You can not use your csc-account to authenticate to your databases. The databases requires their own username and password that you can manage when you create a new database instance or you can add, remove and modify the database user accounts after the database creation. It is important that you create strong passwords for your database accounts..

## Database security
All database instances are running in their dedicated virtual machines, the reason for this is to minimse the risks careless users affect other users that take their security seriously.

The DBaaS admins are allowed to shutdown, lock, or firewall database instances that are suspected to be used malliously, as well as users from using the service. 

Internal Beta: The database instances data are note encyrpted.
Possible production: The database data is encrypted at rest.

## Backups

Internal Beta: Backups are stored unencrypted in Allas.
Production: The backups are stored encrypted in Allas. The backups are automatedly deleted after 90 days. The backups are unencrypted on the database instances if and when a database is restoed from backups.
