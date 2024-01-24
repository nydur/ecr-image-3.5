# 3.5 Step-by-step how to create an image to be deployed to AWS ECR

## Step 1

`aws ecr get-login-password --region ap-southeast-1`

This will generate a long string of characters for the password

## Step 2

`aws ecr get-login-password --region ap-southeast-1 |`\
`docker login --username AWS --password-stdin <aws_account_id>.dkr.ecr.ap-southeast-1.amazonaws.com`

This will confirm if login have been successful

## Step 3

`docker images`

Lists out the available images on the machine to re-tag in a later step

## Step 4

Login into the AWS console to create a private repository with the ECR service

## Step 5

`docker tag <IMAGE_REPOSITORY:TAG> <aws_account_id>.dkr.ecr.ap-southeast-1.amazonaws.com/<ecr_repository_name>:TAG`

`IMAGE_REPOSITORY`& `TAG` is retrieved from Step 3\
`ecr_repository_name` is retrieved from the newly created ECR repository

## Step 6

`docker push <aws_account_id>.dkr.ecr.ap-southeast-1.amazonaws.com/<ecr_repository_name>:TAG`

This will upload the newly tagged image onto the repository

## Final step

If the push is successful, an image of the file will be in the uploaded into the repository. Refresh the ECR console to confirm.
