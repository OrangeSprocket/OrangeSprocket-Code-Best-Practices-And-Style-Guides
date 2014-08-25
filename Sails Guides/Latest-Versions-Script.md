sudo npm uninstall -g sails; sudo npm uninstall sails; sudo npm uninstall -g sails-mysql; sudo npm uninstall sails-mysql; sudo npm install -g sails@0.10.4; sudo npm install sails@0.10.4; sudo npm install -g sails-mysql@0.10.6; sudo npm install sails-mysql@0.10.6


###Too Many Files Error:

Enter this is command prompt

launchctl limit maxfiles 2048 2048 && ulimit -n 2048
