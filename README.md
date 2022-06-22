<h1>Study Guide for Terraform Associate Exam</h1>

<h2>Which IaC tool does not use state files to manage its cloud resources?</h2>

<h3>Answer</h3> GCP Deployment Manager and AWS CloudFormation

<h3>Explanation</h3>

GCP and CloudFormation are cloud-native solutions and there is no state file, or at least it is abstracted away so you don't have to manage or think about it

Cloud Agnostic solutions like Terraform and Plumi require a state file since state has to be portable.

Most cloud service providers, will have a native solution and the managing state will be abstracted away within their online service and you'll never be able to download or move the state file around.

With the exception of Oracle Cloud which is powered by Terraform.

<h2>In order to authenticate to Terraform Cloud what is recommended for local development?</h2>

<h3>Answer</h3> terraform login

<h3>Explanation</h3>

Terraform Login command can be used to automatically obtain and save an API token for Terraform Cloud, Terraform Enterprise, or any other host that offers Terraform services.

https://www.terraform.io/docs/cli/commands/login.html

This is the recommended way to connect to terraform

<h2>Terraform Enterprise Air-gapped environment is designed to run in a network with no internet or outside connectivity</h2>

<h3>Answer</h3> True

<h3>Explanation</h3>

What is Air Gap?

Air Gap or disconnected network is a network security measure employed on one or more computers to ensure that a secure computer network is physically isolated from unsecured networks e.g. Public Internet

https://www.hashicorp.com/blog/deploying-terraform-enterprise-in-airgapped-environments

<h2>What is the general order of a terraform lifecycle?</h2>

<h3>Answer</h3> init > fmt > validate > plan > apply > destroy

<h2>Terraform is a cloud-agnostic tool that can deploy to multiple cloud providers and including anything that has an API such as Kubernetes and Postgres?</h2>

<h3>Answer</h3> True

<h3>Explanation</h3> https://www.terraform.io/intro/use-cases.html#multi-cloud-deployment

<h2>What HashiCorp service can be used alongside Terraform to inject secrets to protect a developer's local enviroment?</h2>

<h3>Answer</h3> Vault

<h3>Explanation</h3> Vault allows you to centralized the management of secrets from various secrets repositories. You can use Vault to pull sensitive credentials at the time of terraform apply.

This tutorial on HashiCorp Learn shows how to use secrets. https://learn.hashicorp.com/tutorials/terraform/secrets-vault?in=terraform/security










