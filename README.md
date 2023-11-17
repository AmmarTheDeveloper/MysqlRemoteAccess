# Mysql Remote Access Setup & Configuration

### Super User In MySQL
we have to create a root or superUser in MySQL for managing users.
but we don't need to create it because when we download mysql by default it is created named as root.

### SuperUser :
a user that has all access to grant permissions to access any other user to the database or perform queries on particular database or table or on all databases or all tables or only peroform particular query on a database or table . like select , delete , update etc.

### Creating A User In MysqL

for Remote accessing our database first we need to create a user in MySQL.

### Query For Creating User
```
CREATE  USER username@"host"  IDENTIFIED BY password.
```
#### Explanation
here  username is the username of the user is going to be created.
here host is a ip or host of the user from where it will going to access the database. if we want to give access from any device to access my database use "%" at the place of host. or if we want to give a access on particular machine so pass there the laptops
 ip address.
and at the place of the password we write password from that password our database will be accessed

### Checking User Created Or Not

we have seen how to create a user now we have check our user is created or not. for checking we have following query.

mysql have predefined database named as mysql. in mysql database we have predefined table named as user. where our users details are stored.

### Query For Checking User


```
USE mysql;
SELECT user, host  from user;
```
#### OR :

```
SELECT user, host from mysql.user;
```
we can't see password because it is stored in hashed form. if we want to see password then use following command.

#### Command For Checking Password 

```
SELECT user , host , authenticaiton_string from mysql.user;
```

### Deleting User
if we want to delete a user we use drop command 
```
DROP USER user@"host"
```

### Granting Permission For Database.

we have seen how to create a user and see it is created or not. now  we have to see how can we give permission to a particular user  to access our database so for that we have grant command for giving access of our particular database  or table.

query for giving all command access on a particular database and on it's all tables.

### Grant Command

```
GRANT ALL PRIVILEGES ON database_name.* TO username@"host"
```
**ALL PRIVILEGES** means the user have access to perform all queries
username and host is the username of the user and host of it which we have created before using grant command.

**database.** * means a  particular database and it's all tables.
if we want to give a particular table access we  use following query.

#### Granting Particular Table Access
```
GRANT ALL PRIVILEGES ON database_name.table_name TO username@"host"
```
for giving a particular query access on a user we perform this command.

### Granting Particular Command Access
```
GRANT SELECT , UPDATE on database_name.* TO username@"host"
```
You Can See  All Privileges List Here 
[https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html](https://dev.mysql.com/doc/refman/8.0/en/privileges-provided.html)

### Flush Privileges Command
After Granting A Permission We Have To Perform Flush Privileges Command.

Because it reloads the grant tables in the mysql database. Enabling the changes to take effect without reloading or restarting MySQL service.

```
FLUSH PRIVILEGESE;
```
### Checking Permissions Given To  A Particular User
we have granted permission to a user Then we have to check it is worked or not After performing Flush command.
```
SHOW GRANTS FOR username@"host"
```
### Revoke Command
if we want to get back given permission from a user we use revoke command.
for removing all commands access on a particular table
```
REVOKE ALL PRIVILEGES ON database_name.table_name FROM username@"host"
```
#### OR
for removing particular command access on a particular table
```
REVOKE SELECT , UPDATE ON database_name.table_name FROM username@"host"
```
#### OR
for removing all commands access on all tables
```
REVOKE ALL PRIVILEGES ON database_name.* FROM username@"host"
```

### MySQL Configuration
we have do some configuration in mysql for giving remote access of our database.
#### Steps For Mysql Configuration
> 1. Open File Explorer And On TaskBar Click On View Then Check The Hidden Files Checkbox\

> 2. Then Open  ProgramData Folder Present In C: Drive

> 3. Then Open MySqL Folder Then Go To MySQL Server Folder Then Find my.ini File

> 4. Then Open It In notepad++(Run Notepad as administrator)

> 5. Then Find [mysqld] in my.ini File After Opening

> 6. Then at the next line of [mysqld] if **bind-adress**  is present then update it's value else add this line

```
bind-address=0.0.0.0
```
> 7. Then Save It

### Accessing Mysql From Another Machine

go to another machine(Laptop Or Pc) from which you are going to access the database.

##### OPEN CMD

> 1. Find This Folder In Your Computer "C:\Program Files\MySQL\MySQL Server *.*\bin" (here * is your mysql version) Copy That Location

> 2. Write This Command In Cmd cd **"C:\Program Files\MySQL\MySQL Server 8.0\bin"**

> 3. Perform This Command

```
mysql -u username -h "host"  -p password
```

> 4. At the place of host provide IpAddress of the machine where database is actually present.

###  THANK YOU 

 





