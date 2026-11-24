# aws-import-existing-s3-bucket

# Objectives
    1. Find an S3 Bucket that already exists
    2. Import existing bucket into terraform management without changing it
    3. Get terraform plan to report no changes are needed
    4. Delete the imported bucket

Configure AWS CLI

aws configure --profile challange

Enter Access key & secret

Enter AWS Region

Enter output format; none or json

List available buckets

aws s3api list-buckets --profile challange

Create the terraform files; provider.tf, main.tf, variables.tf

terraform init
terraform plan # No changes ...snip...

create the import.tf import block

import.tf

import {
  to = aws_s3_bucket.bucket_id
  id = "<bucket-name>"
}

main.tf

resource "aws_s3_bucket" "bucket_id" {

}

terraform fmt

terraform init

terraform plan

show state as planned for execution

terraform state show aws_s3_bucket.bucket_id

terraform apply

clean-up

terraform destroy
