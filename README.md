# ECS Tutorial

## Install ecs-cli

```bash
sudo curl -o /usr/local/bin/ecs-cli https://amazon-ecs-cli.s3.amazonaws.com/ecs-cli-darwin-amd64-latest
sudo chmod +x /usr/local/bin/ecs-cli
ecs-cli --version
```

Select fargate for launch-type and deploy

```bash
ecs-cli configure --region ap-northeast-1 --cluster ecs-tutorial default-launch-type FARGATE --config-name ecs-tutorial
```

Put the key pair `ecs-tutorial.pem` created by ec2 console in `~/.ssh`

```bash
ecs-cli up --keypair ecs-tutorial --capability-iam --size 2 --instance-type t2.medium
ecs-cli compose --project-name ecs-tutorial service up
```

Confirm at [http://127.0.0.1:80](http://127.0.0.1:80)
