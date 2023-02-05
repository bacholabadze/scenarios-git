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

--------------------------------------------------------------------

Prettier output?
git log --graph

Git gives us the possibility to connect multiple parameters in one command.
clear && git log --oneline --graph

---------------------------------------------------------------------

FORMATING

Git allows us to use special formatting to print exactly what we want.

Sometimes your log is very plain. If this is your case and you would like to have more colorful output, use --decorate parameter.

A few examples which we combine into a working command:

%Cblue - switch output text to blue

%Creset - resets the color to default

%H - commit hash. Preferable is to use short hash with %h.

%an - who commited the changes

%ad - date of commit. For scripting purposes you can use UNIX timestamp - %at.

%s - commit message

How to format our commad to use these?

git log --pretty - this is how we start.

Please remember about q ;)

So let's try

clear && git log --graph --pretty="%C(yellow) Hash: %h %C(blue)Date: %ad %C(red) Message: %s " --date=human

Please, go through the command and understand all arguments.

Let's test some different ideas. Try to guess what the command output will be, before you execute them!

clear && git log --graph --pretty="%ad" --date=short

For better clarity you can add format to parameter

git log --graph --pretty=format:"%ad" --date=short

It will do the same. Here are another examples.

clear && git log --graph --pretty="%ad"

clear && git log --graph --pretty="%at"

clear && git log --graph --pretty="%as"

clear && git log --graph --pretty="%C(bold blue)%h"

clear && git log --graph --pretty="%C(bold blue)%h %Cred%s %C(Yellow)by %an"

Another example found on the Internet

clear && git log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit

But... Will you enter this command every single time? No? What you need is on the next page :)

---------------------------------------------------------------------

Git config and aliases
You can create the aliases for your most commonly used commands.

Previously, we used very long command. Let's create an alias for it. We need to add it to the git config file. Of course logical will be to add it to global table.

git config --global alias.lg 'log --color --graph --pretty="%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit'

We instruct git that we want to change configuration (config), on global table (--global) and we configure alias called lg (alias.lg). The alias itself is inside the '' section.

Now you can execute your alias

clear && git lg

--------------------------------------------------------------------

Querying
Or more useful functionality - searching through git log.

You already know how to make your git log beautiful and how to format the output. But all the time we used all information from log. How to narrow the search?

We have a few possibilities.

clear && git log --author="John Doe" will show all commits done by specific author.

clear && git log --author="John Doe\|Joe Smith" - with this regex we asked for all commits authored by these two people.

And now a little bit of theory
It is a good practice to have standards of creating messages for commits. There are a lot of examples in the Internet. Most of them propose to use kind of identifier. When we work with tools like Jira, we have amazing identifier given by the tool - Jira ticket number. So our commit message should look similar to:

JIRA-1234 my commit message

And voila! we have identifier, we can even attach it to Jira itself (by plugins). And use it... for searching through git log!

clear && git log --grep="JIRA-1234"

Theory ends :)
Another way is to look at logs for specific file.

clear && git log -- testfile-01

clear && git log -- testfile-02 branchfile-01

Please notice the --. This way we inform git that we have files, not branches in mind.

We can compare two branches

clear && git log master..second-branch

clear && git log second-branch..master

Please, notice the differences between those two!!

Previously we tried to look for "merge" messages. There is better way.

clear && git log --merges

So, how to exclude merge commits:

clear && git log --no-merges

In our example it will not work very well, but we can search using dates

clear && git log --after=2021-4-21

clear && git log --before=2021-4-21

clear && git log --before 2021-4-30 --after=2021-4-1

clear && git log --after=yesterday

on the end, the easiest thing. We can limit number of returned commits

clear && git log -1

clear && git log -3

And also we can mix search functionalitites

clear && git log -1 --grep="JIRA"

clear && git log -5 --grep="commit" --oneline

Please notice revert message, without commit. hm... Please, check why we see it?

---------------------------------------------------------------------

git log --oneline
git log -p
git --stat
git shortlog
git log --graph
git log --oneline --graph
