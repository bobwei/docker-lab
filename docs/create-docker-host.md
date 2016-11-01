# Single Docker Host

This ia a hands-on note with docker.

Please [setup your aws config](./aws-cli-config.md) before creating instances.

After setting up aws config, then you can provision a docker machine like below with ec2

```
docker-machine create \
  --driver amazonec2 \
  --amazonec2-access-key $(aws configure get aws_access_key_id) \
  --amazonec2-secret-key $(aws configure get aws_secret_access_key) \
  --amazonec2-region us-west-2 \
  --amazonec2-vpc-id vpc-e4c8008d \
  --amazonec2-zone c \
  --amazonec2-subnet-id subnet-006ace59 \
  --amazonec2-security-group launch-wizard-9 \
  --amazonec2-instance-type t2.small \
  --amazonec2-root-size 64 \
  vr-fe-docker-lab
```

Some commands you may need :

```
aws ec2 describe-vpcs
aws ec2 describe-subnets
aws ec2 describe-security-groups
```

Once provisioning a docker machine, you can see it here

```
docker-machine ls
```

Response

```
NAME               ACTIVE   DRIVER      STATE     URL                        SWARM   DOCKER    ERRORS
vr-fe-docker-lab   *        amazonec2   Running   tcp://54.213.25.108:2376           v1.12.1
```

Connect to Docker Host

```
eval $(docker-machine env vr-fe-docker-lab)
```

```
docker ps
```


## Reference

* [AWS Configure](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)
* [Docker Machine Driver for AWS](https://docs.docker.com/machine/drivers/aws/)
