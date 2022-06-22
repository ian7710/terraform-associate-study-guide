<h1>Study Guide for Terraform Associate Exam</h1>

<h2>Which IaC tool does not use state files to manage its cloud resources?</h2>

<h3>Answer:</h3> GCP Deployment Manager and AWS CloudFormation

<h3>Explanation</h3>

GCP and CloudFormation are cloud-native solutions and there is no state file, or at least it is abstracted away so you don't have to manage or think about it

Cloud Agnostic solutions like Terraform and Plumi require a state file since state has to be portable.

Most cloud service providers, will have a native solution and the managing state will be abstracted away within their online service and you'll never be able to download or move the state file around.

With the exception of Oracle Cloud which is powered by Terraform.




