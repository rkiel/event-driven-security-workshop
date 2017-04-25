## AWS CLI

# OS X

Create the project

```unix
cd ~/GitHub/rkiel
git clone git@github.com:rkiel/aws-cli.git
cd aws-cli
```

# AWS Console

Create a new user

* click *IAM*
* click *Users*
* click *Create New Users*
* enter `aws-cli`

Generate credentials

* check *Generate an access key for each user*
* click *Create*
* click *Download Credentials*

Grant user permissions

* click *Users*
* click *aws-cli*
* click *Permissions*
* click *Attach Policy*
* click *AdministratorAccess*
* click *Attach Policy*

# OS X

Parse out the AWS credentials

```unix
grep aws-cli ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $2}' > aws_access_key_id.txt
grep aws-cli ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $3}' > aws_secret_access_key.txt
```

Start up vagrant

```unix
vagrant up

vagrant ssh aws

cd /vagrant
```

Use AWS CLI

```unix
aws s3 ls

aws s3api create-bucket --bucket MY_COOL_NEW_WEBSITE.COM --region us-west-2
```
