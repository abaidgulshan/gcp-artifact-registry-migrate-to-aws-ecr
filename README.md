# 🚀 GCP Artifact Docker Registry Migrate to AWS ECR 

These command and steps used to migrate GCP Artifact Docker Registry Migrate to AWS ECR

Table of Contents
=================

   * [Prerequisites 🛠️](#prerequisites-️)
   * [Usage 📋](#usage-)


## Prerequisites 🛠️

Before you begin, make sure you have the following:

1. **AWS CLI Credentials and Configure**: Ensure you have AWS CLI and credentials configured with the necessary permissions to create resources.
2. **GCP Gcloud cli Credentials and Configure**: Ensure you have GCP Gcloud CLI and credentials configured with the necessary permissions to create resources.

## Usage 📋

1. **Clone this repository to your local machine:**
     ```
       git clone https://github.com/abaidgulshan/gcp-artifact-registry-migrate-to-aws-ecr
       cd gcp-artifact-registry-migrate-to-aws-ecr/
    ```

2. **Commands for Pull GCP Artifactory docker images:**
  * The following command going to create a download script for GCP artifact docker images locally on Ec2 instance of utility-images repository
    * `gcloud artifacts docker images list us-central1-docker.pkg.dev/GCPprojectID/Artifact-registry-Name --include-tags  | awk '(NR>1) && ($2!~/none/) {print "docker pull " $1"@"$2}' > download-gcp-artifacts-images.sh`
  * Run following above created script to download images locally
    ```
    ./download-gcp-artifacts-utility-images.sh
    ./download-gcp-artifacts-gcf-artifacts.sh
    ```
  * Create AWS ECR private repo via AWS web console
  * Create a list of ECR repos according to GCP tags and upload it to AWS ECR, example
    * `docker tag us-central1-docker.pkg.dev/GCPprojectID/Artifact-registry-Name:latest  012345678991.dkr.ecr.us-east-2.amazonaws.com/ECRRepoName:latest`

