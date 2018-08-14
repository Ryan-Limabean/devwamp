# dev.wamp read me file

## What is dev.wamp?
It's a homebrew WAMP aimed to let you easily switch between different PHP versions. dev.wamp currently includes:

* apache 2.4
* php 5.3 to 7.0
* maria db 10.1
* mysql notifier 1.1
* papercut (fake smtp server)

## Installation
I've made install.bat to help automate the installation as much as possible. There are still a couple of things you need to do manually after running it.

Before running install.bat, I would recommend uninstalling any other versions of wamp or xamp or other apache and mysql services on your system.

Before uninstalling wamp I would recommend creating an archive of the c:\wamp\www\ dir (because c:\wamp\www\ will be obliterated by uninstalling wamp!). It's important to archive the contents of your www dir separately so that you can restore it easily using "extract to..." (otherwise there will be complications caused by copying long paths - ie node modules).

Also important to dump any MySQL databases you might have before uninstalling WAMP.

dev.wamp is designed to run from c:\dev.wamp\ so make sure you are working in that directory. When you are ready you can right click install.bat and run as administrator.

## Prerequisites
A Windows PC (only tested on Windows 10 so far).

## Manual installation
You can attempt to install dev.wamp manually without using install.bat and I'm not going to write out detailed instructions right now so just read the bat file and try to make sense of what it's doing.

### PHP CLI
PHP 7.0 will automatically be added the PATH variable during install.bat. If you have any other PHP paths in PATH variable you should remove them. You can also manually change PHP 7.0 to whichever version you prefer.

### Adding more PHP versions
I believe you'll need 64 bit non thread safe versions which can be downloaded from the following URL:
http://windows.php.net/downloads/releases/archives/

Look for a file named like this:
php-x.x.x-nts-Win32-VCxx-x64.zip

The rest you can work out yourself.

## Usage
You can use the mysql notifier in the system tray to start/stop/restart apache or maria db. Otherwise it works more or less just like wamp.

Each version of php has it's own directory with its own php.ini file.

There are wildcard vhosts setup already so if you go to 56.phpinfo.dev it will serve c:\dev.wamp\www\phpinfo\index.php using php 5.6, likewise 70.phpinfo.dev will use php 7.0. The vhost ??.*.dev should work for any project in the www directory. But you can also easily add your own vhosts using whichever version of PHP you desire.

## SSL/HTTPS
HTTPS is possible, just look at the HTTP(S)://LOCALHOST example in httpd-dev.wamp.conf. You won't get green padlock though because it's self-signed.

## Caveats
There is an issue with older versions of CodeIgniter when using mod rewrite to hide index.php in the URL. As of now the only suggested fix is to add a question mark and QSA, like this:
RewriteRule ^(.*)$ /index.php?/$1 [QSA,L]

## Troubleshooting
If Apache service doesn't start then there is most likely an error in the configs/vhosts. Open "Event View" and goto "Windows Logs" for error messages.

## Support for Linux
Nope.

In theory it should be easy to create dev.lamp but I'll leave that for someone else to do.

## Licence
dev.wamp itself is open source, but all original licenses still apply for all the included software packages.