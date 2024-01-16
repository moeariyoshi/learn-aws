# learn-aws

See Terraform also: https://github.com/moeariyoshi/learn-terraform

## Setting up AWS CLI
https://docs.aws.amazon.com/cli/latest/userguide/cli-services-iam.html

### Create User Group
```
$ aws iam create-group --group-name MyIamGroup
{
    "Group": {
        "GroupName": "MyIamGroup",
        "CreateDate": "2018-12-14T03:03:52.834Z",
        "GroupId": "AGPAJNUJ2W4IJVEXAMPLE",
        "Arn": "arn:aws:iam::123456789012:group/MyIamGroup",
        "Path": "/"
    }
}

```
### Create IAM user
```
$ aws iam create-user --user-name MyUser
{
    "User": {
        "UserName": "MyUser",
        "Path": "/",
        "CreateDate": "2018-12-14T03:13:02.581Z",
        "UserId": "AIDAJY2PE5XUZ4EXAMPLE",
        "Arn": "arn:aws:iam::123456789012:user/MyUser"
    }
}
```
### Add user to group
```
$ aws iam add-user-to-group --user-name MyUser --group-name MyIamGroup
$ aws iam get-group --group-name MyIamGroup # Verify that is worked
```
### Add policy to user 
```
$ aws iam attach-user-policy --user-name MyUser --policy-arn $POLICYARN
```
### Set initial password
```
$ aws iam create-login-profile --user-name MyUser --password My!User1Login8P@ssword --password-reset-required
```
### Change password 
```
$ aws iam update-login-profile --user-name MyUser --password My!User1ADifferentP@ssword
```
### Access key for a user 

Create: 
```
$ aws iam create-access-key --user-name MyUser
```
Delete:
```
$ aws iam delete-access-key --user-name MyUser --access-key-id AKIAIOSFODNN7EXAMPLE
```

### Set up profile

`aws configure --profile profile-name`

### Changing default profile
`$ export AWS_DEFAULT_PROFILE=profile_name`
