# Ec2 

## Create a Single keypair for ssh
```
aws ec2 create-key-pair --key-name $KEYNAME
```

## get a single keypair id 
```
aws ec2 describe-key-pairs  --key-name $KEYNAME --query 'KeyPairs[*].KeyPairId' --output text
```


