# How to Create a SSH Key

Table of contents

- [ Creating a ssh key ](#create-ssh-key)
- [ Set SSH key usage through SSH config ](#setting-ssh-config)
- [ Use for Github Personal Key ](#github-personal-key)
- [ Use for Github Deploy Key ](#github-deploy-key)

<br><br><br>

### **1. Check for existing SSH keys**

<a name="create-ssh-key"></a>

You should check for existing SSH keys on your local computer. You can use an existing SSH key, or you may create an additional one.

**For Windows:**

Open a command prompt, and run:

    cd %userprofile%/.ssh
    dir id_*

**For Linux:**

Open a terminal and run the following:

    cd ~/.ssh
    ls -la ~/.ssh/

If you see "No such file or directory, then there aren't any existing keys: go to step 3.

If there are existing keys, you may want to use them; go to either SSH user keys for personal use or SSH access keys for system use.

### **2. Back up old SSH keys**

If you have existing SSH keys, but you don't want to use them when connecting, you should back those up.

Do this in a terminal/command prompt on your local computer, by running:

** For Windows:**

    mkdir key_backup
    copy id_rsa\* key_backup

**For Linux:**

    mkdir key_backup
    cp id_rsa\* key_backup

### **3. Generate a new SSH key**

If you don't have an existing SSH key that you wish to use, generate one as follows:

1.  In a terminal/ command prompt as administrator, run:

        ssh-keygen -t rsa -C "your_email@example.com"

    Associating the key with your email address helps you to identify the key later on.
    Note that for windows based system the `ssh-keygen` command is only available if you have already installed Git (with Git Bash).

    You'll see a response similar to this:

2.  Just press `<Enter>` to accept the default location and file name. If the .ssh directory doesn't exist, the system creates one for you.

        Generating public/private rsa key pair.
        Enter file in which to save the key (~/.ssh/id_rsa):

3.  Enter, and re-enter, a passphrase when prompted.

You're done! Now go to either SSH user keys for personal use or SSH access keys for system use.

## Use ssh key as a pem key

<a name="setting-up-pem"></a>
To use ssh key as a pem key simply rename the private ssh key file `(the file not containing .pub)` with .pem

1.  [ Create SSH key ](#create-ssh-key)

2.  Rename the key that doesn't end with .pub to repo-name.deploy.pem

3.  Update key file permission:

        sudo chmod 400 repo-name.deploy.pem

## Set SSH key usage through SSH config

<a name="setting-ssh-config"></a>

To use an ssh/pem key configure the ssh config.

1.  [ Create SSH key ](#create-ssh-key)
2.  Create config file inside `~/.ssh` folder

        touch config

3.  Set config file permission

        sudo chmod 644 ./config

4.  Add entry in config file

        Host sample.com
        Hostname sample.com
        IdentityFile ~/.ssh/sample.pem

## Use for Github Personal Key

<a name="github-personal-key"></a>

1.  [ Create SSH key on the deployment host machine ](#create-ssh-key)
2.  Add the content from the public key file i.e. .pub to your remote repository user access keys,
    in github for example navigate through the following menu:
    1. [ Settings ](https://github.com/settings/profile)
    2. [ SSH and GPG keys ](https://github.com/settings/keys)
    3. New SSH Keys
3.  Set the workspace to use the SSH remote url of the Github repo to access by SSH key not the HTTPS remote.
    To check which github remote url is used:

        git remote -v

## Use for Github Deploy Key

<a name="github-deploy-key"></a>

1.  [ Create SSH key on the deployment host machine ](#create-ssh-key)
2.  [ Configure the ssh key created in step 1 as pem file](#setting-up-pem)
3.  [ Set the ssh usage through ssh config](#setting-ssh-config)
4.  Add the content from the public key file i.e. .pub to your remote repository,

    in github for example navigate through the following menu:

    1. Settings ( usually `https://github.com/{user}/{repository}/settings` )
    2. Deploy keys ( usually `https://github.com/{user}/{repository}/settings/keys` )
    3. Add deploy keys

5.  Set the workspace to use the SSH remote url of the Github repo to access by SSH key not the HTTPS remote.
    To check which github remote url is used:

         git remote -v
