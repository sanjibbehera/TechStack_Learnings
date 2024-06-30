## What is EKS?


## AWS EKS and IAM Role
- we create a ServiceAccount for the Kubernetes Pod, in the annotations of this ServiceAccount we specify an ARN of an IAM role that this Pod should use for authentication in AWS (authorization, that is, checking what actions you can perform in AWS, will be performed at the level of AWS itself in the IAM using an IAM Policy that is connected to your IAM Role).
- EKS generates a JWT token, which indicates that the “sender” of this token is indeed a valid EKS user, and EKS confirms this with its certificate
- a process from the Pod uses this token to authenticate to AWS IAM and execute the AssumeRole operation
- already on behalf of this IAM Role, this process of the Pod performs the necessary actions with the AWS API