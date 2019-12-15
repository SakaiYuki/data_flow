# Docker for AWS

https://docs.docker.com/docker-for-aws/

## Prerequisite

- [awscli](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv1.html)

## Constraints

Only verified in:

- ap-northeast-1
- t3a.micro

## Usage

```
$ git clone git@github.com:SakaiYuki/docker-for-aws.git
$ cd data_flow
$ export BUCKETNAME=<bucketname>
$ aws s3 cp Docker.tmpl s3://$BUCKETNAME/
$ aws cloudformation create-stack \
  --stack-name docker-for-aws \
  --template-url https://s3-`aws configure get region`.amazonaws.com/$BUCKETNAME/Docker.tmpl \
  --parameters ParameterKey=KeyName,ParameterValue=<AWS::EC2::KeyPair::KeyName> \
  --capabilities CAPABILITY_IAM
```
