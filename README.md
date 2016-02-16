# Aria Example Blueprint

This repository contains a TOSCA blueprint for installing the [Paypal Pizza Store](https://github.com/paypal/rest-api-sample-app-nodejs/) example application.

The contents of this repository:
 - A Vagrantfile for booting a vagrant box for testing.
 - The Aria Blueprint that you will execute
 - The supporting scripts.

This example blueprint creates:

- A Mongo Database
- A NodeJS Server
- A Javascript Application

## How to Execute this Blueprint

### Pre-step 1: Start the vagrant box

`vagrant up`

### Pre-step 2: Prepare the vagrant box

`sudo apt-get install python-dev gcc -y && wget https://bootstrap.pypa.io/get-pip.py && sudo python get-pip.py && sudo pip install virtualenvwrapper && virtualenv aria && source aria/bin/activate && pip install aria-tosca==0.6 && cd /vagrant`

### Step 1: Initialize

`aria init -p local-blueprint.yaml`

or

`aria init -p multicloud-blueprint.yaml -i inputs/multicloud.yaml`

### Step 2: Install

Lets run the `install` workflow:

`aria execute -w install --task-retries 100 --task-retry-interval 10 --task-thread-pool-size 20`

### Step 3: Uninstall

To uninstall the application we run the `uninstall` workflow:

`aria execute -w uninstall --task-retries 100 --task-retry-interval 10 --task-thread-pool-size 20`