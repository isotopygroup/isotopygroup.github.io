# Git

## Install Git

```
sudo apt update
sudo apt install git
```

## Setup for Multiple Accounts
Git commits are signed with a username and email.
These variables are stored in several configuration files with different scopes.
To prevent mixing up user details when working with multiple GitHub accounts we will set the user variables in each repository.
Additionally, we will set the global user variables to null values so that an error is thrown in new repositories reminding us to set the values.

The global configuration file is located in the user home directory `~/.gitconfig`.
The following commands will set the global user variables to the empty string:

```
git config --global user.name ''
git config --global user.email ''
```

To set the user variables for a specific repository use the following commands from within the repository:

```
git config user.name USER_NAME
git config user.email USER_PUBLIC_EMAIL
```

Note that the GitHub email settings page displays an automatically generated email address which can be used to keep the email address associated with your GitHub account private.

To list current values of all GitHub variables use:

```
git config -l
```
