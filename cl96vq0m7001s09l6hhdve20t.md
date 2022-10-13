# How to Print Environment Variables in Linux

But really, those are the variables that are just specific to your current system environment such as the currently logged-in user will be stored inside the "USER" variable.

Still confused? no worries. I will walk you through a brief understanding of environment variables and then jump to various ways to print them.

# What are Environment Variables?
One of the most basic environment variables that you encounter on a daily basis is `HOSTNAME`. 

## All caps
Most of the environment variables are pre-defined by the system and are global variables so you'll encounter them often written in all caps.

## Main goal of `ENVs`
Suppose you are a programmer and your code needs to have access to your database key which should never be shared in public.
So what options do you have while sharing the entire code on Git? Wrap the database key to the environment variable.
This way you can set instructions on Git as "if you want to make this code work, interchange this variable with your database key."
Of course, this was the one way of using environment variables. So let's have a look at some common environment variables in Linux.

Some most commonly used ENVs are:
* `HOME`: Shows home directory for the current user
* `HOSTNAME`: Contains Hostname of your system
* `UID`:	Stores unique ID of the user
* `SHELL`:	Shows the path to the shell which is being used currently
* `BASH_VERSION`:	Contains version currently used bash instance
* `HISTFILE`:	Path of the file where the history of commands is saved
* `TERM`:	Shows the type of log-in terminal you're using
* `PATH`:	Shows path of commands and directories are separated by columns.

Above list is not exhaustive.

## Print Environment Variables in Linux
There are many ways of doing this.
### `printenv`
Prints EVs from **currently used shell** only.
Proper syntax of `printenv` is:
```bash
printenv ENV
```
so, for example:
```bash
printenv HOSTNAME
```
will print your hostname.

You can also stack multiple `ENVs` at once. This way value of each `ENV` will start from `\n` ( newline ).

You can get list of all `ENVs` registered in your **local** by issuing:
```bash
printenv
```
command:

![printenv.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665654433604/I1jNZxEZd.png align="left")
