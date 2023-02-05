.gitignore
Git gives us the possibility to control what will be synchronized with remote and what will be not.

This is realized by file named .gitignore

Let's see what we have. In the background system initialized the repo and do some work. Nothing is staged, nothing is commited.

cd test && ls -al

git status

We don't want to commit

seconddirectory{{}} directory and its content
neveringit file
But these are in git status, right?

Let's create gitignore file

touch .gitignore

echo neveringit >> .gitignore

echo seconddirectory >> .gitignore

cat .gitignore

Let'ss check the status again

git status

Ok, we are ready to run

git add .

and

git status

And commit

git commit -a -m "first commit"

And now we can run git status to see what is changed.

Yes, we can confirm, what shouldn't be in remote isn't on the list.

______________________________________________________________________

More configs
Ok, so now we are able to ignore some specified files.

Now we want the file with the same name neveringit from firstdirectory to be sent to remote. Maybe it is only an example how it should work. Some instruction for other people for example.

Let's create additional file then.

touch firstdirectory/neveringit

And its content

echo "this file has to go to git!" >> firstdirectory/neveringit

Ok. do

git status

git add . and then again

git status

Well. It is not what we want.

Ok, first, we know, the filename we used itself works for all directories in repo. Git has strict rules how these 'masks' work, please check in documentation if you want to have it more complicated.

The good practice is to be as most specific as possible. So, what we need, really is:

**/neveringit
!firstdirectory/neveringit
First line says explicitly - all files anywhere in the structure (and now it is clear, readable and visible

In second line the exlamation mark negates the pattern. Another words, we negate the deny and allow this file to be sent to remote.

Ok, let's check.

sed -i 's/neveringit/**\/neveringit/g' .gitignore

echo '!firstdirectory/neveringit' >> .gitignore

And check

cat .gitignore

Ok, to be sure, let's do an experiment.

mkdir thirddirectory && echo "gotogit" > thirddirectory/togit && echo "not for git!" > thirddirectory/neveringit

After a

git add . let's run

git status

Yep, we can confirm, neveringit file is never added to commit, except only one situation: when we forced it.
