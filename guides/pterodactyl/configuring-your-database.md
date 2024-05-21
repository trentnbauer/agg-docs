# Configuring your Node Database

<table data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Time Required</td><td>10 minutes</td></tr><tr><td>Difficulty</td><td>Low</td></tr></tbody></table>

## Purpose of this database

This database is separate from the Panel's database and included in my Wings compose file. This ensures that the data stored is segregated from the Panel DB (reducing risk of corrupting the panel) and allowing for the game server to connect to a DB on the same host, which will result in better performance.

## Create the Wings DB user

Firstly, we need to create the Wings user. This is unfortunately a manual step that needs to be done on the DB but its pretty straight forward

1. Log into Portainer and navigate to Stacks
2. Open the Pterodactyl Panel stack and take note of the MYSQL\_PASS\_ROOT variable
3. Use a password manager to generate a password for the 'Wings' user, please ensure you save these credentials
4. Scroll down and click on the database container
5. Click on Console, then Connect
6. Type `mysql -u root -p`, hit enter and input the Root password from step 2
7.  Copy and paste the below text into Notepad, and change update the password field

    ```sql
    CREATE USER 'wings'@'%' IDENTIFIED BY '<<YOUR PASSWORD HERE>>';
    GRANT ALL PRIVILEGES ON *.* TO 'wings'@'%' WITH GRANT OPTION;
    exit
    ```
8. Copy and paste each individual line into Portainer and hit enter

_This will create a 'wings' user that can connect from anywhere ( % ) with admin privileges... Keep these creds safe!_

## Add the Database into Pterodactyl

Now we need to add the Database into Pterodactyl. Luckily - this is much easier to do!

1. Log into your Pterodactyl Panel as an administrator
2. Hit the settings cogs / admin button in the top right
3. On the left, click on Databases
4. Fill out the database per below and hit Create

| Field        | Data                                                                                         |
| ------------ | -------------------------------------------------------------------------------------------- |
| Name         | A friendly name for easy viewing purposes. I recommend using the same as the nodes hostname. |
| Host         | Your server hostname / IP                                                                    |
| Port         | The [PORT\_DB stack variable](creating-a-new-wings-node.md)                                  |
| Username     | wings                                                                                        |
| Password     | The password you generated above                                                             |
| Linked Nodes | The Node the database is stored on                                                           |

_Please note: Your Wings nodes will need to be able to comminute with your Database. This means that you will need them in the same LAN / Network, or some form of VPN or port forwarding (not recommended...) to allow them to communicate._

## Test creating a Database

1. Open an existing game server, or create a new Minecraft server (please ensure it has a database limit of more than 1)
2. Click on Databases
3. Click on 'New database'
4. Give it a name and hit 'Create'
5. Click on the eye to view the database details, such as the username, password and connection string. This information is needed to configure your game server to use the DB
