# ☁️ AWS CLI

## Install

```bash
# Download the AWS CLI v2 installation file
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

# Unzip the package (Install unzip if not already installed)
sudo apt install -y unzip
unzip awscliv2.zip

# Run the install script
sudo ./aws/install

# Cleanup
rm awscliv2.zip
rm -rf aws
```

## Verify

```bash
aws --version
```

## Common Commands

```bash
aws configure                      # Configure AWS CLI (Access Key, Secret Key, Region)
aws configure list                 # List configuration and credentials
aws s3 ls                          # List all S3 buckets
aws s3 mb s3://bucket-name         # Create a new S3 bucket
aws s3 rb s3://bucket-name         # Remove an empty S3 bucket
aws ec2 describe-instances         # List EC2 instances
aws iam list-users                 # List IAM users
aws lambda list-functions          # List all Lambda functions
```

## Uninstall

```bash
# Locate the current version
which aws

# Remove the installation directory and symlinks (Default paths)
sudo rm /usr/local/bin/aws
sudo rm /usr/local/bin/aws_completer
sudo rm -rf /usr/local/aws-cli
```
