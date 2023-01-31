Anyway, we have 4 files in stage. Let's remove testfile-01

git rm --cached testfile-01

Great! We removed one file from stage. What about three others?

Yes, we can do the same command like before and change the name of the file in the command. But what if we have 10 files? 100?

git rm --cached -r .

please notice, we used . to say everything from here and -r which means recursive.

---------------------------------

Restore previous state of the file
Our files were staged again and even commited in the background.

Let's see our commit

git log

About git log we will talk in another scenario.

We have all 4 files ready to be commited, but unfortunately, we don't want those changes.

First, let's check what is in the file testfile-01

cat testfile-01

git checkout testfile-01

cat testfile-01

git status

We succesfully reset the file to the state from previous commit, using git checkout. In this way we do the checkout of the last indexed state of this file on current branch.

In similar way like in some scenarios before, we can remove all changes in one short command. Let's do it.

git checkout .

--------------------------------------

