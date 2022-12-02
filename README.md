# pupdate - install new puppet and clean up old versions


## SYNOPSIS:

Script(s) to update from various Puppet agent versions to newer versions.
(Currently the newer version is 7).


## USAGE:

    ./pupdate

There are currently no command-line flags or options.

It's probably best to clone the repository, change directories into the cloned repo,
and run the program from there at least until you're familiar with the **post-run files**
mentioned below.


## CONFIGURATION:

There is currently no configuration file for the main program.

There is a directory for **post-run files** - that is, files to be run after the main program.

**pupdate** looks in the current directory for a subdirectory called **pupdate-post** in
which to find the *appropriate* files for the *current system* on which it's being run.
Any of those files found will be checked for being executable. If so, they are run.

There's one file, '**generic**', which is always deemed appropriate. Other files named
for the *distribution family* (for example 'redhat' or 'debian'), for the *distribution*
(for example 'centos', 'amazon', or 'ubuntu'), or for the *distribution and version*
(with a dash between them, such as 'ubuntu-bionic' or 'cloudlinux-7').

For the RedHat family of distributions only the major version number is used. A file named
something like 'centos-7.9' won't be run.

For Debian-derived systems the version's nickname is what's supported rather than the
version number. This fits with a lot of Debian culture and is how Puppet differentiates
distribution versions for their packages.


## Examples

If you're on Ubuntu Bionic Beaver, the list of files to be searched will be:

    ./pupdate-post/generic
    ./pupdate-post/debian
    ./pupdate-post/ubuntu
    ./pupdate-post/ubuntu-bionic

If you're on Amazon Linux 2:

    ./pupdate-post/generic
    ./pupdate-post/redhat
    ./pupdate-post/amazon
    ./pupdate-post/amazon-2


## DEPENDENCIES

- currently only runs on Linux
- Perl 5 installed at /usr/bin/perl
- working network connection
- must be run as root
- access to install packages with apt or yum


## BUGS

Let us know what you find.


## AUTHOR

Christopher E. Stith
cPanel, LLC (a WebPros, LLC company)
[christopher.stith@webpros.com](mailto:christopher.stith@webpros.com)


## MAINTAINERS

- cPanel, LLC's SRE team, "Crow T. Robot"
- The cPanel Sysadmin team
- cPanel's IT security team, "Spy vs. Spy"

[IT combined ops team email](mailto:cpanel-sadmin@webpros.com "Probably the better contact.")


## COPYRIGHT

Copyright 2021, cPanel, LLC


## SEE ALSO

- [perl](https://perl.org)
- [puppet](https://www.puppet.com)


## RESOURCES

- [Puppet 7.5 system requirements](https://puppet.com/docs/puppet/7.5/system_requirements.html)
- [Puppet apt repo](https://apt.puppetlabs.com/)
- [Puppet yum repo](https://yum.puppet.com/puppet7/el/7/x86_64/)
- [Puppet advice on installing release packages outside of apt](https://puppet.com/docs/puppet/5.5/puppet_platform.html#apt-based-systems)


