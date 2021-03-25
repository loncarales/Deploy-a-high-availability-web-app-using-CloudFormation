# Deploy a high-availability web app using CloudFormation

## Prepare config so AWS CLI can communicate with the API

```bash
export AWS_ACCESS_KEY_ID=<aws_access_key>
export AWS_SECRET_ACCESS_KEY=<aws_secret_access_key>
export AWS_DEFAULT_REGION=us-west-2
```

First let's create a Network Infrastructure. We can use the helper scripts provided.

## Create Udagram-Network Cloud Formation Stack

```bash
$ ./create.sh Udagram-Network Udagram-network.yaml Udagram-network.json
```

After the first part of AWS inftrastructure is created we can deploy the rest: IAM Role, Security Groups, Launch Configuration and Load Balancer.

## Create Udagram-Servers Cloud Formation Stack

```bash
$ ./create.sh Udagram-Servers Udagram-servers.yaml Udagram-servers.json
```

## Delete Cloud Formation Stacks

```bash
$ aws cloudformation delete-stack --stack-name Udagram-Servers
$ aws cloudformation delete-stack --stack-name Udagram-Network
```
