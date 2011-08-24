Redmine on OpenShift
=========================
 
Redmine is a flexible project management web application. Written using Ruby on Rails framework, it is cross-platform and cross-database.

Redmine is open source and released under the terms of the GNU General Public License v2 (GPL).

More information can be found on the official Redmine set (www.redmine.org)
Running on OpenShift
--------------------

Create an account at http://openshift.redhat.com/

Create a rails application

	rhc-create-app -a redmine -t rack-1.1

Add mysql support to your application
    
	rhc-ctl-app -a redmine -e add-mysql-5.1
Make a note of the username, password, and host name as you will need to use these to login to the mysql database

Add this upstream rails quickstart repo

	cd redmine
	rm -rf *
	git remote add upstream -m master git://github.com/gshipley/redmine-openshift-quickstart.git
	git pull -s recursive -X theirs upstream master

Add your database username and password 

	vi config/database.yml
	git commit -a -m "Adding mysql auth information"

Then push the repo upstream

	git push

That's it, you can now checkout your application at:

	http://redmine-$yourlogin.rhcloud.com

Use the following to login to your new redmine application running on openshift

	username: admin
	password: admin

