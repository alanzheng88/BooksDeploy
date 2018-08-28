# Books

### Setup
```
vagrant plugin install vagrant-aws
vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
vagrant up --provider=aws
```

### Temporary solution for running backend server
```
source .env-development && DATABASE_URL="$DATABASE_URL" PORT=8000 python36 manage.py run
```
