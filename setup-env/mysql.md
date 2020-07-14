# MySQL

## Installing MySQL

```bash
sudo apt update
sudo apt install mysql-server
```

If no configuration options were presented during installation run the following command to configure security options.

```bash
sudo mysql_secure_installation
```

By default it seems the authentication method is to use `auth_socket` which is linked to a linux user.

```bash
mysql -u root -p  # this cmd won't work
sudo mysql  # linux root has access to mysql server root
```

After logging in with the linux root user you can change the authentication method:

```sql
mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'password';
mysql> FLUSH PRIVILEGES;
```

Now you can login with

```bash
mysql -u root -p
```

Alternatively create a new user with root privileges.

```sql
mysql> CREATE USER 'user'@'localhost' IDENTIFIED BY 'password';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' WITH GRANT OPTION;
```

## Installing MySQL Workbench

Install MySQL workbench from the Ubuntu Software app. You may need to change the app permissions to read/write passwords.

