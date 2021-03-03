# Zeus-Bot-Info
All information necessary for using Z E U S

(Last updated on Match 3rd 2021)

### Basic Info
Z E U S is a custom discord bot made for Olympus server network. 
Bot owner is A R E Z#9064 (174228239382740995). 
Zeus is used in [Custom-Strike](https://discord.gg/6AbkcN8) and [Arez Kingdom](https://discord.gg/ywbNFy8).
Zeus is used for syncing roles across all Olympus servers, storing roles in the database and easily assign/remove roles from users using commands.

### Structure

#### Server structure
All servers that Zeus bot is used in (bot is private, you can't add this bot to your server) is split in two categories: master server and children servers.
Master server is a server that used as an example when, for example, syncing roles. Bot looks at roles in master server, copies roles from master servers, and changes all roles in children servers according to the ones in master server.

#### Role structure
Roles that can be used for assignment are stored in a config file. 
Every role has:
- name
- role ID on master server
- permissions level

Role name is not the role name on Discord. This name is used in commands, for example `+modder @Stew#1902`. Actualy role name on Discord is `🔨 Custom-Striker`. 

Role ID is stored for syncing purpose. Let's say we changed role name from `🔨 Custom-Striker` to `🔨 Custom striker`. When this change is made, role ID is not changed, only role name property. Now, if this change was made on master server (not on children servers), bot will go through all children server and change role name from `🔨 Custom-Striker` to `🔨 Custom striker` by finding role on every child server with old name.

Permission level of each role allows to have a hierarchy system as mentioned above. For example, let's say that my only role is `🔨 Custom-Striker`. Let's say that this role has permission level 1. I can manage any role that has a permissions level of 0. So, if i want to assign to someone `🥈 2020 Service Medal` role that has permission level 0, bot will allow this assignment. If i want to assign a role that has higher permission level, for example `⚔️ Knight` which has permission level 3, bot will not allow this assignment and will notify the executor that user misses permission level. If user has no roles in the database, same notification will be sent.

*Note: permission level strucuture may be changed in the soon future*

### !fullsync functionality
!fullsync is a powerful command which can only be done by certain users. !fullsync command deletes all roles on children servers (hence removing ALL channel permissions), copies roles from master server and creates them in all children servers. After that, bot goes through every user in the database and assigns their roles. This command also deletes all roles from user that don't have some/any roles in the database. This should only be done manually when needed.

### !sync functionality
!sync is a softer command compared to !fullsync. This command goes through each role in master server, and for each role finds its copy on children server *by name* (if you change a role name on children server, bot will skip the role and will neither delete it nor edit it), and if it was successfully found, edits all of its properties to the ones that are on master server. Then bot again goes through the database and assigns roles. This command doesn't delete roles from users that got assigned a role manually.

### !syncUser functionality (prototype, may not work)


### + / - commands
Role assignment is main bot functionality. This command fully depends on role properties so make sure to read the **Role structure** paragraph above.

After + or - sign you should place role name that you want to be added/removed to/from user. Not to provide not the role name on Discord, but role name from config. To check all valid role names, use `!help` command or read **Available roles** paragraph below. To check permission level of a certain role and what roles can it assign, use `![role name]` command.

Parameter of the command is a valid discord mention or a valid discord user ID. Bot may not have any mutual servers with the mentioned user to be able to assign them a role (this specific part may be useful against raid users to assign them `🔒 Gulag 17` role even if they leave the server).

First part is checking if a mention is provided / ID is a valid discord ID. If parameter is not valid, error is thrown.

If user ID is valid, bot will check if this user is in the database. If user exists there, bot will automatically sync the roles from the database, excluding the role that is trying to be added/removed in the command. 

After that, bot checks if user has the permission to run this command. Executor cannot modify his/her roles (to not remove `🔒 Gulag 17` from themselves for example), cannot modify roles bot roles, and (not sure?) cannot edit roles of users whose role permission level is higher than permission level of command executor. Role that is assigned/removed should be lower than permission level of command executor (for now, in the future certain roles will have permission to assign only specified list of roles)

If command passed all tests, bots adds the user to the database if user wasn't present there, or modifies the user from the database with new roles. After database manipulation, a user sync is run again to assign newly modified roles only.


### Available roles
Currently these are the roles that Zeus bot can manage: 2018, 2019, 2020, gulag, emperor, lord, knight, squire, noble, verified, modder, rep, sus. Each role has a ID assigned to
