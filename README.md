
# AWS Cloud Cost Optimization - Identifying Stale Resources
## Identifying Stale EBS Snapshots
In this example Project, we'll create a Lambda function to identify and delete unattached EBS snapshots, which are no longer associated with any active EC2 instance. This helps optimize storage costs by removing unnecessary snapshots.

### Description:
In this Lambda function, it retrieves all EBS snapshots owned by the account and compiles a list of currently active EC2 instances, including both running and stopped instances. The function then evaluates each snapshot, focusing on those that have been inactive for at least 30 days. An **"inactive"** snapshot is defined as **one either not associated with any active volume or linked to an active volume not currently associated with any EC2 instance**. If a snapshot meets these criteria, it is deleted, facilitating the efficient management of storage costs by removing unnecessary and outdated EBS snapshots.


## AWS Configurations Steps For This Project

### Create a Lambda Function:

- Go to the AWS Lambda Console.
- Click on "Create function."
- Choose "Author from scratch."
- Enter a name for your function (e.g., "snap-management").
- Choose the runtime as "Python" (ensure it matches the Python version used in your code).
- In the "Function code" section, paste your Python code.
- Set the handler as lambda_function.lambda_handler.

### Adjust IAM Permissions:

Ensure that the Lambda function's execution role has the necessary permissions.

In your case, it needs permissions for `ec2:DescribeSnapshots`, `ec2:DescribeInstances`, `ec2:DescribeVolumes`, and `ec2:DeleteSnapshot`.

### Save and Test:

Save your Lambda function.
You can **manually** test the function by clicking **"Test"** in the Lambda Console.

