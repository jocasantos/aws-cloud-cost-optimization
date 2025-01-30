# AWS Cloud Cost Optimization
Identifying Stale Resources

## Identifying Stale EBS Snapshots
In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

### Description:
- The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

## Demo Guide

### Create a new instance and create a snapshot
- Create a new instance
- Create a Snapshot from the instance (you can access the snapshot console in the EC2 dashboard)

### Create the Lambda function
- Select "Author from scratch"
- Name your function "example-function-name"
- Choose Python Runtime
- Select "create function"
- In the Tab "Code", replace the Python function with the code in <ebs-stale-snapshots.py>
- Select "Deploy"
- Select "Test" and create a test named "test"
- Select "Test" again
- In the tab "Configuration" edit "General Configuration" and edit "Timeout" 3s to 10s 
> Note: In the future try to keep this time as low as possible, AWS will charge by the second

