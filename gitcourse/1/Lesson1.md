Check your system
First, let's see if we have Git installed. We can do it on different ways

dpkg -l | grep git

The ii in the list means (if there are packages installed, you should see this mark) that the package is correctly installed and available.

apt list git -a

apt-cache pkgnames git

----------------------------

Install Git
In order to install Git, you can use multiple ways, we will use apt command.

apt install -y git

----------------------------
git --version

This command will show you version of installed package.
----------------------------

