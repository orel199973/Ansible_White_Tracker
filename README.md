# CI_CD_Ansible  <img src="https://avatars.githubusercontent.com/u/1507452?s=200&v=4" width="40" height="40"/>  


This playbook will create and provision all web servers within the network with the weight tracker app: https://developer.okta.com/blog/2020/06/01/node-postgres-weight-tracker.
This repo you will find:
* Weight Tracker app deployed with ansible, using roles, variables and different modules.
* YAML to write ansible configurations.
* A controller machine which deploy the app to different enviroments (staging and production) using a single playbook.


# steps:
* Install ansible on ubuntu 18.04 with the commands in this site: [Installation Guide](https://www.linuxtechi.com/how-to-install-ansible-on-ubuntu/) 
* Create ssh key and copy to remote machine by this command: ssh-keygen
* Configure remote machine to enable ansible to run it.
* Edit the hosts file: /etc/hosts and /etc/ansible/hosts - In the hosts file you can define your working groups, such as "staging" or "prodn" and assign to each group their unique properties. Here we will just store there the IPs of the relevant machines. 
create your groups like this:
![image](https://user-images.githubusercontent.com/71599740/140193516-accd29a2-bba2-41ed-9851-5507b68c81fc.png)
![image](https://user-images.githubusercontent.com/71599740/140191877-8247a808-7c1c-463b-a5b5-92f85a3fddef.png)
* Run a test to verify a connection exists with managed hosts
* Copy the key to the agents by using ssh-copy-id <path-to-file> user@hostname command.
* Verify connection
* Make a new directory called enviroment
* In enviroment directory make 2 directory called - staging and prod
* In staging and prod make a new directory called "group_vars" 
* In each "group_vars" directory create a YML file there with the same name as your group name( enviroment name) that store the .env variables. for example - PGHOST,OKTA, POSTGRESQL, and IP ADDRESS HOST.
* In enviroment directory create a new playbook - mkdir playbook -> nano playbook.yml
* Run playbook : ansible-Playbook *Your Play book YAML file* --extra-vars "group=*your group name* var_file_path=*enviroment/<my group name>/group_vars/variable file name*"
  
For example:
ansible-playbook playbook.yml --extra-vars "group=staging var_file_path=/home/Inbalevi0707/environments/staging/group_vars/staging.yml"

  
* You can add few flags for debugging: </br>
This command will show debugging output ansible-playbook -i hosts <location of the hosts> <location of playbook> -u <username> -vvv
This command will ask you to confirm each step ansible-playbook -i hosts <location of the hosts> <location of playbook> -u <username> --step
This command will start the playbook on the requested task name ansible-playbook -i hosts <location of the hosts> <location of playbook> -u <username> --start-at-task:"<name of the task>"



# Node.js Weight Tracker

![Demo](docs/build-weight-tracker-app-demo.gif)

This sample application demonstrates the following technologies.

* [hapi](https://hapi.dev) - a wonderful Node.js application framework
* [PostgreSQL](https://www.postgresql.org/) - a popular relational database
* [Postgres](https://github.com/porsager/postgres) - a new PostgreSQL client for Node.js
* [Vue.js](https://vuejs.org/) - a popular front-end library
* [Bulma](https://bulma.io/) - a great CSS framework based on Flexbox
* [EJS](https://ejs.co/) - a great template library for server-side HTML templates

**Requirements:**

* [Node.js](https://nodejs.org/) 12.x or higher
* [PostgreSQL](https://www.postgresql.org/) (can be installed locally using Docker)
* [Free Okta developer account](https://developer.okta.com/) for account registration, login

## Install and Configuration

1. Clone or download source files
1. Run `npm install` to install dependencies
1. If you don't already have PostgreSQL, set up using Docker
1. Create a [free Okta developer account](https://developer.okta.com/) and add a web application for this app
1. Copy `.env.sample` to `.env` and change the `OKTA_*` values to your application
1. Initialize the PostgreSQL database by running `npm run initdb`
1. Run `npm run dev` to start Node.js

The associated blog post goes into more detail on how to set up PostgreSQL with Docker and how to configure your Okta account.

