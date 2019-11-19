# General Notes

## Best Practices


### Root User Account
Use the root user only to create your first IAM user. Then securely lock away the root user credentials.

### AWS Signature

Access keys consist of two parts: an access key ID (for example, AKIAIOSFODNN7EXAMPLE) and a secret access key (for example, wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY). You use access keys to sign programmatic requests that you make to AWS if you use AWS CLI commands (using the SDKs) or using AWS API operations.

One critical aspect of using any AWS REST API call is the signature used to authenticate the request. This signature is vital if you wish to allow only authenticated users to access your data.

This allows for verification of:
1> the requestor’s identity
2> in-transit data integrity protection
3> protection against reuse of the signed portions of the request for replay attempts. 

![awssignature](images/awssignature.png)
