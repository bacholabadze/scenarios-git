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
