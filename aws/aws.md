# AWS Cloud architecture & services

## AWS CLI

* aws ec2 describe-instances --profile user --> usage of profile from aws credentials on local machine
* aws ec2 describe-images --owners amazon --filters "Name=name,Values=amzn2-ami-hvm-*-x86_64-gp2" --query 'reverse(sort_by(Images, &CreationDate))[].Name' -->
searches amazon linux 2 AMI name according to name pattern. Then it sorts with Name, Creation date descending. 
* aws s3 ls s3://bucket-name --recursive --human-readable --summarize --> list content of the bucket-name

### S3 CLI
* aws s3 sync s3://acc_one_s3_bucket s3://acc_two_s3_bucket/acc_two_folder --profile aws-profile --> allows to copy content
of acc_one_s3_bucket S3 bucket from one AWS account to folder in S3 bucket acc_two_s3_bucket/acc_two_folder on another AWS
account. Permissions on the SOURCE bucket must be granted by using Canonical ID to list objects and read them.
 
## AWS basic components

###VPC

#### Blogs / Online Articles
* [Deep dive into AWS VPC And VPC peering](https://medium.com/faun/deep-dive-into-aws-vpc-and-vpc-peering-3ea919bd367a)
* [VPC sharing: A new approach to multiple accounts and VPC management](https://aws.amazon.com/blogs/networking-and-content-delivery/vpc-sharing-a-new-approach-to-multiple-accounts-and-vpc-management/)

## AWS Services

### IAM

* [Generating Least Privileged IAM Roles for CloudFormation and Service Catalog with cfn-leaprog](https://stelligent.com/2020/05/15/generating-least-privileged-iam-roles-for-cloudformation-and-service-catalog-with-cfn-leaprog/)

### Lambda

* [Lambda Asynchronous invocation](https://docs.aws.amazon.com/lambda/latest/dg/invocation-async.html)
* [How AWS Lambda team made my two years old talk completely irrelevant](https://medium.com/@serhatcan/how-aws-lambda-team-made-my-two-years-old-talk-completely-irrelevant-1c74c528ca78)


### ECS

#### Blogs / Online Articles
* [Gentle Introduction to How AWS ECS Works with Example Tutorial](https://medium.com/boltops/gentle-introduction-to-how-aws-ecs-works-with-example-tutorial-cea3d27ce63d)


### ECR

### DynamoDB
* [DynamoDB Transactions Examples](https://www.alexdebrie.com/posts/dynamodb-transactions)

* [7 ways to do async message processing in AWS](https://winterwindsoftware.com/aws-async-message-services)