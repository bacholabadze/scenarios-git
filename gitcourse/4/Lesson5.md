Text editor for create message for commit
Until now we add messages to commits using -m parameter. Let's do something different. We have repo prepared and some files are in stage, so let's commit one of them

cd test

git commit testfile-01

As you see, the default editor was executed and we can add commit using it. Feel free to add message and commit, or exit.

Default editor
Let's check if we have anything configured

git config --global --list | grep editor

No, we do not have anything configured.

What we've done? We asked git to show us the whole configuration in global space. We can use system and local too. Local obviously means the configuration of this specific repo. Also, we grep the output to find information about editor only.

Let's change it to the best editor ever - vi!

git config --global core.editor vi

Check the config again

git config --global --list | grep editor

All looks good, so now it is the time to commit our next file

git commit testfile-02

This time we used vi!

Ah, vi ;P Do you wish to quit the editor? Click ESC key and then write :q!
