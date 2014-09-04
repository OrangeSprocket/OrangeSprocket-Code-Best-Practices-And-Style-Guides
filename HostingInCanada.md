#Connect and Install

We host in canada on http://www.netelligent.ca/datacentre/

ssh root@234.234.234.234

--enter password

#Install Node on the server

Follow this [Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-run-a-node-js-app-on-centos-6-4-64bit)

#Clone the code you want to host

Git clone the repo (You may need to add [ssh keys](https://help.github.com/articles/generating-ssh-keys)) 

cd into your repo

sudo npm install -g forever (Needed to run the server)

npm install -g npm (Update to the latest npm version)

sudo npm install -g sails

sudo npm install -g bower

bower install

(You may need: bower --allow-root install pure normalize-css angular html5shiv angular-bootstrap angular-ui-router angular-cookies underscore bluebird) or something similar

forever node app.js

#Then set up the database

##Need to install mysql

```
rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm
yum install mysql.`root -i` yum-plugin-replace
yum replace mysql --replace-with mysql55w
yum install mysql
```

```
yum replace mysql --replace-with mysql55w
yum install mysql55w mysql55w-server
service mysqld start
```

###Need to set up cron jobs to back up the data

Something like this: 0 1 * * * root mysqldump -u webapp -p4570rangeSpr0cket --all-databases | gzip > /var/www/dbs/database_`date +"\%m-\%d-\%h"`.sql.gz
that file exists where
and is called what
   
#Set up the repo to host in production

touch local.js
vi config/local.js 

insert this code:

```
module.exports.models = {
  environment: 'production',
  connection: 'production',
  migrate: 'alter',
  port: 80
};
```

vi config/connections.js 

```
module.exports.connections = {
  localhost: {
    adapter: 'sails-mysql',
    host: 'localhost',
    user: 'root',
    password: '',
    database: 'Offtober'
  },

  production: {
    adapter: 'sails-mysql',
    host: 'localhost',
    user: 'root',
    password: '',
    database: 'Offtober'
  }
};
```

vi config/env/production.js 

Note: In here, uncomment the lines:

```
models: {
     connection: 'production'
   },
```
and...
```
port:80
```

sails lift --prod --verbose (This will get the server running on port 80)



Need to have cron jobs to save the db to a folder twice a day or something

#Then set up the dns settings
