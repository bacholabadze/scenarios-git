Config's must have
let's run

git config --global --list


--system - table relevant for the whole machine

--global - for the current user

--local (default) for the current repository


Ok, let's make some entries.

git config --global user.name "John Doe"

git config --global user.email johndoe@myemail.com

[!] We created our "personality". Of course it can be overwritten with the --local in any of repos.



git config --global core.editor vim


git config --list -a ll settings are printed.

git config --list --global - only --global table is listed

git config user.name - selected record is printed.

--------------------------------------------------

What is inside?

ls -al .git

So, what is what? Let's explain the important files /directories.

hooks directory contains all custom hooks. These are small (usually) scripts which have to be executed before commit, or after, before push, etc.

branches - this is deprecated. Don't think about it anymore.

HEAD - pointer to the current branch and its latest commit.

config - configuration file for the repository.

info - the place where you stage the files using git add.

refs - the current state of the whole repo.

objects - commits, trees and blobs are stored here. May be very big.

logs - quite self explanatory.

description - description of the repository.

Ok, so, what we have in config file?

cat .git/config

-----------------------------------------------------

ice to have things
Let's come back to our configuration.

Maybe we will add some colors?

git config --global color.status auto

git config --global color.branch auto

git config --global color.interactive auto

git config --global color.diff auto

git config --global alias.adog "log --all --decorate --oneline --graph"

Explanation. A dog is very popular way to remember the most useful set of parameters for git log.

git config --list
