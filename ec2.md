# Ec2 

## Create a Single keypair for ssh
```
aws ec2 create-key-pair --key-name $KEYNAME
```

## get a single keypair id 
```
aws ec2 describe-key-pairs  --key-name $KEYNAME --query 'KeyPairs[*].KeyPairId' --output text
```

## create a security group 
```
aws ec2 create-security-group --group-name ssh-http-https-all --description "ssh-http-https-all"
```

## add the rules to security group created 
```
aws ec2   authorize-security-group-ingress --group-name ssh-http-https-all --ip-permissions IpProtocol=tcp,FromPort=22,ToPort=22,IpRanges='[{CidrIp=0.0.0.0/0}]',Ipv6Ranges='[{CidrIpv6=::/0}]' IpProtocol=tcp,FromPort=80,ToPort=80,IpRanges='[{CidrIp=0.0.0.0/0}]',Ipv6Ranges='[{CidrIpv6=::/0}]' IpProtocol=tcp,FromPort=443,ToPort=443,IpRanges='[{CidrIp=0.0.0.0/0}]',Ipv6Ranges='[{CidrIpv6=::/0}]'
```



# create a ubuntu 18.04 ARM 64 instance 

while createing the security group ids is good idea if its a non default vpc ( For a nondefault VPC, you must use security group IDs instead )
```
aws ec2 run-instances --image-id ami-0987943c813a8426b --instance-type t2.micro --key-name $KEYNAME --security-groups "ssh-http-https-all"
```






