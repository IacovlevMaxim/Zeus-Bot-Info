# Zeus-Bot-Info
All information necessary for using Z E U S

(Last updated on Match 2nd 2021)

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

Permission level of each role allows to have a hierarchy system as mentioned above. For example, let's say that my only role is `🔨 Custom-Striker`. Let's say that this role has permission level 1. I can manage any role that has a permissions level of 0. So, if i want to assign to someone `🥈 2020 Service Medal` role that has permission level 0, bot will allow this assignment. If i want to assign 

*Note: permission level strucuture may be changed in the soon future*

### Available roles
Currently these are the roles that Zeus bot can manage: 2018, 2019, 2020, gulag, emperor, lord, knight, squire, noble, verified, modder, rep, sus. Each role has a ID assigned to
