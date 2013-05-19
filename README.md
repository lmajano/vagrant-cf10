# ColdFusion 10 Vagrant Environment
## And [Cloudy With A Chance Of Tests](https://github.com/mhenke/Cloudy-With-A-Chance-Of-Tests)

This is a [Vagrant](http://vagrantup.com) project for [ColdFusion 10](http://www.adobe.com/products/coldfusion-family.html) development and includes Cloudy With A Chance Of Tests.

## Prerequisites
1. [Vagrant](http://downloads.vagrantup.com) installed
 - Requires [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed
1. [Ruby](http://www.ruby-lang.org/en/downloads) installed 
1. [Git](http://git-scm.com/downloads) installed  
1. [Librarian-Chef](https://github.com/applicationsonline/librarian-chef) installed
 - ```gem install librarian-chef```
1. [Downloaded](https://www.adobe.com/cfusion/tdrc/index.cfm?product=coldfusion) 
 - **32bit Linux ColdFusion 10** installer from Adobe 
 - copy to directory `/vagrant-cf10/ColdFusion_10_WWEJ_linux32.bin`

## Quick Setup
```
    $ git clone git@github.com:mhenke/vagrant-cf10.git
    $ cd vagrant-cf10
    $ librarian-chef install
    $ vagrant up
```

## Quick Usage ( ANT )
 Copy your code to your **web root** ```/vagrant-cf10/wwwroot``` 
```
	$ vagrant ssh
	$ cd /vagrant/wwwroot
	$ ant -p build.xml #shows all targets
	$ ant #runs default target
```

## Quick Usage ( JENKINS )
1. Uncomment line with ```jenkins_workspace``` in ```build.properties``` located in your web root 
1. (optional) Setup [**Source Code Management** for Cloudy](http://192.168.33.10:8080/job/cloudy/configure)
 - default is a Github project called [cf-datatables](https://github.com/mhenke/cf-datatables/)
1. Go you [http://192.168.33.10:8080/job/cloudy](http://192.168.33.10:8080/job/cloudy)
1. Click **Build Now**
1. To see the build output select **Console Output**

## Detailed Setup
1. Open the command prompt ( **not git bash** )
1. Clone this repository to your Vagrant project directory, i.e. `/vagrant-cf10`
1. Run `librarian-chef install` in the Vagrant project directory
1. Download the 32bit Linux ColdFusion 10 installer from Adobe and place it in the Vagrant project directory, i.e. `//vagrant-cf10/ColdFusion_10_WWEJ_linux32.bin`
1. Run ```vagrant up```

## Important File Paths
1. Your **web root** is a shared mapping on your host such as ```/vagrant-cf10/wwwroot```
1. When ```vagrant ssh``` into your instance, the web root is ```/vagrant/wwwroot```

## Important URLs
- [ColdFusion Administrator](http://192.168.33.10/CFIDE/administrator) ( login with username: admin, password: vagrant )
- [MxUnit](http://192.168.33.10/mxunit)
- [CFQuery Param Scanner](http://192.168.33.10/qpscanner)
- [VarScoper](http://192.168.33.10/varscoper)
- [Jenkins](http://192.168.33.10:8080)
- [Jenkins - Job - Cloudy](http://192.168.33.10:8080/job/cloudy)

## Installs / Configures
- Adobe ColdFusion 10
- Oracle Java 7
- Jenkins
- Apache
- VIM
- Git
- ANT
- MxUnit
- Cloudy with a Chance of Tests
- CFQuery Param Scanner
- VarScope Scanner

## Error
- vagrant box add fails in Git Bash/Windows
 - DON'T USE GIT BASH
- vagrant ssh on Windows
 - http://docs-v1.vagrantup.com/v1/docs/getting-started/ssh.html
- stdin: is not a tty
 - not really an error, just annoying message
- permissions issue when running ant
 - run ```sudo chmod 777 /opt/coldfusion10/cfusion/wwwroot/WEB-INF/cfclasses/```
- Jenkins Cloudy job configuration feezes on loading http://192.168.33.10:8080/job/cloudy/configure
 - update Jenkins to at least ver. 1.509.1
