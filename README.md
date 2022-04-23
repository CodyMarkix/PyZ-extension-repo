# PlugM, PyZ's plugin manager's main repo

- - -

## Table of Contents
- [PlugM, PyZ's plugin manager's main repo](#plugm-pyzs-plugin-managers-main-repo)
  - [Table of Contents](#table-of-contents)
- [How does it work?](#how-does-it-work)
  - [For end users](#for-end-users)
    - [First-time use](#first-time-use)
  - [Commands:](#commands)
  - [For repo maintainers](#for-repo-maintainers)
    - [Creating a repository](#creating-a-repository)
    - [Adding repositories](#adding-repositories)
    - [Updating](#updating)

# How does it work?

## For end users
PlugM, the plugin manager used for these plugins works similarly to Linux package managers.

### First-time use
After you install PyZ, if you want to start using PlugM, you must first intialize it using `pyz plugm init`. This is only done once and creates some folders and a local repo list and manifest.json.

## Commands:

- `init` - Initializes PlugM - ONLY RUN THIS ONCE
- `update` - Updates the list of available plugins
- `upgrade` - Updates any packages that have available updates.
- `search` - Searches for a plugin
- `install` - Installs a plugin.
- `remove` - Removes a plugin.
- `add-repo` - Adds a repository
- `del-repo` - Removes a repository

## For repo maintainers

### Creating a repository

A PlugM repository can be hosted on pretty much any form of server that can store files. A few examples include.

- A Github/lab repository
- An SFTP server
- A web server

basically anything that can store files and have files be downloaded from via HTTPS.

In every repository, you must store a `MANIFEST.json` file that looks like this.

```json
{
    "plugins": [
        {
            "name": "sample-package",
            "version": "1.0",
            "description": "This is a sample plugin!",
            "file": "sample-package.zip"
        },

        {
            "name": "another-package",
            "version": "1.0",
            "description": "Hey I'm also a plugin!",
            "file": "another-package.zip"
        }
    ]
}
```

Obviously, you can remove the two sample plugins, but every plugin must include:

- Its name
- Its version
- Its description
- Its archive's file name

### Adding repositories

### Updating

The way PlugM updating works is when you update it for the first time, it downloads the MANIFEST.json from this repository

<img src=".readmeassets/update.png" width="600">

and writes it to its own MANIFEST.json, stored on the end-user's computer.

