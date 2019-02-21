# Example of applying CIS Baseline1 and Baseline2 to RHEL7


## Steps
1. This work is based on (MindPointGroup/RHEL7-CIS)[https://github.com/MindPointGroup/RHEL7-CIS]
2. RHEL AMI from Red Hat on AWS
3. You will see a small delay in the middle of the video cast below as the patches are being applied
4. Run the playbook

## Execution 
```
ansible-playbook -v -e "user=ec2-user" --become --key-file "/home/ec2-user/.ssh/id_rsa" playbook.yml
```

## Recording

[![demo](cis-rhel7-example.png)](https://asciinema.org/a/A5HZ6A4G8wyoUI2GSg7Brm2KE?autoplay=1&speed=2)
