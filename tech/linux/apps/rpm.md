https://linuxconfig.org/how-to-list-all-files-installed-by-rpm-package

The easiest way to locate all files installed from RPM package on your system is to check a RPM package manifest which shows all files and location for any particular RPM package. Let's say that I downloaded a telnet-server-1.2-137.1.i586.rpm RPM package from some online source and I wish to see what this package contains and what files will be installed into the system.

rpm -qlp telnet-server-1.2-137.1.i586.rpm

RPM options used:
-q : this is a general rpm query
-l : list package content
-p : package name


To check a content of the RPM package before installation you can do:

rpm -ql telnet
