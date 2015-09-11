## Setting up Homestead

This process is optional, but I highly recommend doing it for developing Orchestra Platform on your local mashine. Homestead give you full access to feature that we can use with Orchestra Platform. You can read the full documentation from [Laravel Homestead](http://laravel.com/docs/5.1/homestead).

Now, if you haven't use Homestead before, you probably need to add the box:

    vagrant box add laravel/homestead

Once you have it downloaded, let run the following command in your project directory.

    composer require --dev "laravel/homestead=^2.1"

Once composer has installed the dependencies, you can start adding Homestead support for your project by running the following command:

    ./vendor/bin/homestead make

> This action will create `Vagrantfile` and `Homestead.yaml` on your project root directory.

### Update Homestead.yaml

The generated `Homestead.yaml` will generally good enough to get you started, but let's open it and inspect the following:

| Key          | Description
|:------------|:---------------------
| ip          | Ensure that `ip` is unique and is not being use by other VM or machine in your intranet.
| hostname    | You can either use the default or customize it based on your preferences.
| name        | You can either use the default or customize it based on your preferences.
| sites       | Make sure you map all the possible domain for your application.
| databases   | Make sure you type in the database name that you want to use for your application.

Here's an example how I configured it on my machine.

```yaml
---
ip: "192.168.50.10"
memory: 2048
cpus: 1
hostname: patio
name: patio
provider: virtualbox

authorize: ~/.ssh/id_rsa.pub

keys:
    - ~/.ssh/id_rsa

folders:
    - map: "/Users/crynobone/Sites/patio"
      to: "/home/vagrant/patio"

sites:
    - map: patio.app
      to: "/home/vagrant/patio/public"

databases:
    - patio

variables:
    - key: APP_ENV
      value: local
    - key: DB_DATABASE
      value: patio
    - key: CACHE_DRIVER
      value: redis
    - key: SESSION_DRIVER
      value: redis
```

> Also take note changes made under `variables`. This as identical to modifying `.env`.

### Provision VM

Now we can start provisioning the VM.

    vagrant up

### Update the Hosts File

Don't forget to add the "domains" for your Nginx sites to the hosts file on your machine! The hosts file will redirect your requests for the local domains into your Homestead environment. On Mac and Linux, this file is located at `/etc/hosts`. On Windows, it is located at `C:\Windows\System32\drivers\etc\hosts`. The lines you add to this file will look like the following:

    192.168.50.10 patio.app

Once you have added the domain to your hosts file, you can access <http://patio.app> via your web browser!
