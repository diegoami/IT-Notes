# CONNECTING AWS

~/amazon$ ssh -i "Diego-Amazon.pem" ubuntu@ec2-52-59-153-136.eu-central-1.compute.amazonaws.com


## TUNNELING

https://eu-central-1.console.aws.amazon.com/ec2/v2/home?region=eu-central-1#Instances:sort=instanceId

ssh -i Diego-Amazon.pem -NL 8123:localhost:9999 ubuntu@ec2-52-59-153-136.eu-central-1.compute.amazonaws.com
https://localhost:8123/


