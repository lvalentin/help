help
====

All the doc and help for using Checkmy Website services.


To run in develpoment mode, you need to do the following :

Have a vagrant installation working on your computer and then :

~~~~
git clone git@github.com:checkmyws/help.git
cd help
vagrant up
vagrant ssh
cd /vagrant/
npm install
bower install
bundle install
~~~~

You're ready to rock :)

~~~~
grunt serve
~~~~

to preview the site
