### Below is a table with commonly used options for both methods.

| Option Syntax               | psql                      | Explanation                                                                                |
| --------------------------- | ------------------------- | ------------------------------------------------------------------------------------------ |
| -s --superuser              | SUPERUSER                 | Add the superuser privilege.                                                               |
| -S --no-superuser           | NOSUPERUSER               | No superuser privilege (default).                                                          |
| -d --createdb               | CREATEDB                  | Allows the user to create databases.                                                       |
| -D --no-createdb            | NOCREATEDB                | Not allowed to create databases (default).                                                 |
| -r --createrole             | CREATEROLE                | Allows the user to make new roles.                                                         |
| -R --no-createrole          | NOCREATEROLE              | Not allowed to create roles (default).                                                     |
| -i --inherit                | INHERIT                   | Automatically inherit the privileges of roles (default).                                   |
| -I --no-inherit             | NOINHERIT                 | Do not inherit privileges of roles.                                                        |
| -l --login                  | LOGIN                     | Allows the user to log into a session with the role name (default).                        |
| -L --no-login               | NOLOGIN                   | Not allowed to log into a session with the role name.                                      |
| --replication               | REPLICATION               | Allows initiating streaming replication and activating/deactivating backup mode.           |
| --no-replication            | NOREPLICATION             | Not allowed to initiate streaming replication or backup mode (default).                    |
| -P --pwprompt               | PASSWORD '[password]'     | Initiates password creation prompt or adds provided password to the user.                  |
| /                           | PASSWORD NULL             | Specifically sets the password to null. Every password authentication fails for this user. |
| -c [number]                 | CONNECTION LIMIT [number] | Sets the maximum number of connections for a user. Default is without limit.               |
| --connection-limit=[number] | CONNECTION LIMIT [number] | Sets the maximum number of connections for a user. Default is without limit.               |

**Table 1:** Options

### Connect to psql prompt as postgres user

```sh
sudo -u postgres psql
```

### List Users

```sh
\du
```

### Create User

```sh
sudo -u postgres createuser -s -d -r --replication --pwprompt [name]
```
