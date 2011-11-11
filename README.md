MULTIPLE PUBLIC SSH KEY ON YOUR MAC OSX
=======================================

Create your ssh keys
--------------------

First you need to create your two ssh key

    $ ssh-keygen -t rsa -C "test1@test.com"
    $ ssh-keygen -t rsa -f ~/.ssh/id_rsa_OTHER_LABEL -C "test2@test.com"

Note: You can use anyname for your public second key


Attach to github
----------------

login in each github account and attach your keys respectively.
What do you gonna attach ?

    $ vim ~/.ssh/id_rsa[YOUR_NAME].pub

copy and paste into the public key field at github page

Create a ssh config file
------------------------
Well, we create two differents ssh keys and attach respectively in github.
Now, we have to create a way to identify the differents github accounts.

Create a config file
   $ touch ~/.ssh/config
   $ vim ~/.ssh/config

example:

    #Default GitHub
    Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
    #Default GitHub
    Host github-company
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_OTHER_LABEL

and save the changes.

How does it works?
------------------

Now, if you wanna create new project, you have to specify the HOST name in the
add remote origin step change.

Example
    $ git init
    $ git commit -m"firt commit"
#now if you use your first one ( normal github )
    $ git remote add origin git@github.com:Company/testing.git
#instead it you want to use the other user just change the HOST name
    $ git remote add origin git@github-COMPANY:Company/testing.git

:)

