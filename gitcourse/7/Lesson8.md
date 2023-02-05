Formatting information from git log
Right now we know how git log works. Well, it is ok, but is there any way to extract some data or format messages? Or even query them?

Yes!

Remember to quit git log with q. If logs are longer than your screen, it always goes to interactive mode.

git log --oneline

--oneline shows only most important info about commits. You have only hash and commit message.

Is this enough? We can argue. But definitely is more clear for high level understanding of previous work. How to make it better we will see soon.



git show command

It shows more details about last (or selected) commit.

But hey! We can do this for all commits!

clear && git log -p

Please remember to use q key to escape and come back to shell.

Some statistics' folks wish to know what amount of work was done in the commit. Git gives this possibility

clear && git log --stat

Now we can clearly see how many lines were added or removed in each commit.

Maybe you wish to see the information sorted by author of the commits?

clear && git shortlog is the answer!


---------------------------------------------------------------------
git log --oneline
git log -p
git --stat
git shortlog
