## Event Driven Security Workshop

# OS X

Create the project

```unix
cd ~/GitHub/rkiel
git clone git@github.com:rkiel/event-driven-security-workshop.git
cd event-driven-security-workshop
```

# AWS Console

Create a new user

* click *IAM*
* click *Users*
* click *Add User*
* enter `security-workshop`

Access Type
* check *Programatic access*
* check *AWS Management Console access*

Generate credentials

* check *Generate an access key for each user*
* click *Create*
* click *Download Credentials*

Grant user permissions

* click *Users*
* click *security-workshop*
* click *Permissions*
* click *Attach Policy*
* click *AdministratorAccess*
* click *Attach Policy*

# OS X

Parse out the AWS credentials

```unix
grep security-workshop ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $1}' > user_name.txt
grep security-workshop ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $2}' > password.txt
grep security-workshop ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $3}' > aws_access_key_id.txt
grep security-workshop ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $4}' > aws_secret_access_key.txt
grep security-workshop ~/Downloads/credentials.csv |awk  -F "\"*,\"*" '{print $5}' > console_login.txt
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
