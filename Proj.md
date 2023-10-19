# Continuous-Integration-on AWS-Cloud

## This is the use of continuious integration pipeline on AWS. The following is the flow of execution :
1. AWS account
2. Code Commit 
   * Create codecommit repo
   * Create iam user with codecommit policy
   * Generate ssh keys locally
   * Exchange keys with iam user
   * Put source code from github repo to cc repository and push
3. Code Artifact
   * Create an IAM user with code artifact access
   * Install AWS CLI, configue
   * Export auth token
   * Update settings .xml file in source code top level directory with below details
   * Update pom.xml file with repo details
4. Setting up Sonar Cloud
   * Create sonar cloud account
   * Generate token
   * Create SSM parameter with sonar details
   * Create Build project
   * Update codebuild role to access SSMparameter
5. Create notification for sns or slack
6. Build Project
   * Upadte pom.xml with artifact version with timestamp
   * Create variable in SSM => parameterstore
   * Create Build Project
   * Update codebuild role to access SSMparameterstore
7. Create Pipeline
   * Codecommit
   * Testcode
   * Build
   * Deploy to s3 bucket
8. Test Pipeline