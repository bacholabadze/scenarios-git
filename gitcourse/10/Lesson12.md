Create tags
The system prepared the repo with a few commits. At this moment we can say "ok, this is what we can treat as full functionality", a snapshot, if you wish.

First, let's go into repo's directory.

cd work

Now, let's check the status and log

git status

git adog

Yes, we see some work done.

We can do lightweight tags or annotated. Honestly, I do not like the first one. I prefer annotated tags as we can see some info there.

The difference here is how these types of tags are build. For lightweight tags git creates something similar to branch that doesn't change.
In case of annotaded tag, git stores it as whole odject in database.

Let's check if we have any tags

git tag

No, we don't.

So we make one!

git tag -a v1.0 -m "version 1.0. initial state"

You can use what you wish for a tag. But good practice is to use v and number which describes the changes from previous tag.
How to create proper tagging strategy - there is many documents about it.

_______________________________________________________________________________________

Check the tags
Ok, now we can check our tags again.

git tag

Yes, one is created. What is inside?

git show v1.0

_________________________________________________________________________________________

More tags and navigation
Right now system creates a few new files and commits them.

So, we will create more tags.

Let's try with checking what we have and the we tag current HEAD.

git adog

As we can see, tag v1.0 is marker somewhere in the middle.

Ok, we do the new tag now.

git tag -a v2.0 -m "version 2.0. A lot of new features"

git tag

git adog

As we can see, now git has two tags.

___________________________________________________________________________________________

Tag by commit
Oh... We just realized... We had to tag our state with v1.5 after the commit for testfile-06...

Now worries, we still can do it.

git adog | grep 'testfile-06' | awk '{print $2}' | head -n1

What happened here?

git adog - this is obvious by now, I hope.

grep 'testfile-06 - this will select entries with message where this filename occurs (not the best way, but in our case it is more than enough).

awk '{print $2}' - with awk we are 'cutting' the output and print only the third (counted from 0) element, where separator (default one) is a space.

head -n1 - on the end we are printing ony the first element (if there is more records with the same name). git log shows commits by descending through date, so this works for us.



commit2tag=$(git adog | grep 'testfile-06' | awk '{print $2}' | head -n1)

To be sure, we confirm if variable contains proper value.

cat $commit2tag

Now we will use this variable for commit.

git tag -a v1.5 -m "version 1.5. Some updates" $commit2tag

git tag

git adog

We succesfully tagged commit from history.

_______________________________________ 

Navigate through tags
Navigation between tags is very easy. We already know the command.

clear && git tag

let's jump to first tag

git checkout v1.0

Ok. We switched. Probably. Let's check.

git adog

Yes, HEAD is on the same commit as tag v1.0.

But...

Where we are on our branch?

git branch

Oh... We are detached from master. Makes sense, we jumped back into past.

Ok. log gives us information where we are. Let's be sure.

git tag

Hm... Not very helpfull, right?

To check what on what tag you are currently on, use

git describe

Or

git describe --tags

to be more exact.

git describe will return info about current tag. If there is no tag created yet, git will throw an error. If we are somewhere in the middle:

commitbetweentags=$(git adog | grep 'testfile-05' | awk '{print $2}' | head -n1)

git checkout $commitbetweentags

git adog

git describe

We see now the tag on which we already started to build our changes.

__________________________________________________________________________________--

Delete tag
Ok, let's go back to the Master branch (what means to the top of our work before the recent change - in our case).

git checkout master

And now we delete v1.0 tag.

git tag -d v1.0

git tag

git adog

Yep, tag is deleted.
