# AWS CLI Config

Setup aws config with your key and secret

```
aws configure
```

Your aws credentials are stored here

```
~/.aws/credentials
```

If you have more than one aws account, you can switch between accounts by setting env

```
export AWS_DEFAULT_PROFILE=my_aws_account
```

If you want to switch to default account every time you open the terminal, you can add the export expression to the ~/.bash_profile
