#Connect and Install

We host in canada on http://www.netelligent.ca/datacentre/

ssh root@234.234.234.234

--enter password

#Install Node on the server

[Tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-and-run-a-node-js-app-on-centos-6-4-64bit)

do that stuff

Git clone the repo (You may need to add ssh keys https://help.github.com/articles/generating-ssh-keys) 

cd repo

sudo npm install -g forever

npm install -g npm

sudo npm install -g sails

forever node app.js

#Then set up the database

##Need to install mysql

rpm -Uvh http://mirror.webtatic.com/yum/el6/latest.rpm
   59  yum install mysql.`root -i` yum-plugin-replace
   60  yum replace mysql --replace-with mysql55w
   61  yum install mysql

yum replace mysql --replace-with mysql55w
   64  yum install mysql55w mysql55w-server
   65  service mysqld start
   
   

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
