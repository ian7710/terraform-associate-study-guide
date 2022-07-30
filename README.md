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

<h2>A DevOps Engineer needs to reference an existing AMI (machine image) for an AWS Virtual machine called example. What would be the correct resource address to assign this AMI to another virtual machine?</h2>

```json
resource "aws_instance" "example" {
  ami = "ami-abc123"
  instance_type = "t2.micro"

  ebs_block_device {
    device_name = "sda2"
    volume_size = 16
  }
  ebs_block_device {
    device_name = "sda3"
    volume_size = 20
  }
}
```

<h3>Answer</h2>

```json
resource "aws_instance" "example2" {
  ami = aws_instance.example.ami
  }
```

<h3>Explanation</h3>

This is correct because we are referencing the resource block

<h2>Not specifying the module version for a module will result in an error?</h2>

```json
module "consul" {
  source = "hashicorp/consul/aws"
}
```
<h3>Answer</h3> True, it will result in an error

<h3>Explanation</h3>
It does not explicitly say in the docs, but if you remove the version then you will see that it will pull the latest stable from Terraform Registy

The real exam had a similar question which is why this is included in the exam pool of questions.

https://www.terraform.io/docs/language/modules/sources.html

<h2>When you want to remove a record tracking a remote object in your state file but have the remote object (eg. Azure Virtual Machine) to still exist, which command do you use?</h2>

<h3>Answer</h3>
terraform state rm

<h3>Explanation</h3>
Usage: terraform state rm [options] ADDRESS...

Terraform will search the state for any instances matching the given resource address, and remove the record of each one so that Terraform will no longer be tracking the corresponding remote objects

https://www.terraform.io/docs/cli/commands/state/rm.html

<h2>What is the purpose of Sentinel with Terraform?</h2>

<h3>Answer</h3>
Sentinel allows you to write policies to validate that your infrastructure is in its expected configuration.

<h3>Explanation</h3>
Sentinel is a Policy as Code tool. You can use it to validate the state of your infrastructure and automate it for remediation to ensure your infrastructure stays compliant.

<a href="https://docs.hashicorp.com/sentinel">Sentinel Documentation</a>

<h2>The following is a valid configuration for a provider?</h2>

```json
terraform {
  providers{
    aws = {
      source = "hashicorp/aws"
      version = "3.58.0"
    }
  }
}

provider "aws" {
  # Configuration options
}
```
<h3>Answer</h3> False

<h3>Explanation</h3>

```json
Each Terraform module must declare which providers it requires, so that Terraform can install and use them. Provider requirements are declared in a required_providers block.

terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
      version = "3.58.0"
    }
  }
}

provider "aws" {
  # Configuration options
}
```

https://www.terraform.io/docs/language/providers/requirements.html#requiring-providers

<h2>You can use -target flag on terraform plan to only affect specific resources.</h2>

<h3>Answer</h3> True

<h3>Explanation</h3>
-target=ADDRESS - Instructs Terraform to focus its planning efforts only on resource instances which match the given address and on any objects that those instances depend on

https://www.terraform.io/docs/cli/commands/plan.html#resource-targeting

<h2>A module needs to have the latest patches applied but not update the major or minor version.

Which of the following will achieve this requirement?</h2>

<h3>Answer</h3>
version = "~> 1.2.0"

<h3>Explanation</h3>
~>: Allows only the rightmost version component to increment. For example, to allow new patch releases within a specific minor release, use the full version number: ~> 1.0.4 will allow installation of 1.0.5 and 1.0.10 but not 1.1.0. This is usually called the pessimistic constraint operator.

https://www.terraform.io/docs/language/expressions/version-constraints.html

<h2>Which is NOT a valid argument for remote-exec?</h2>

<h3>Answer</h3>
interpreter

<h3>Explanation</h3>
interpreter is an argument available to local-exec

The following arguments are supported:

inline - This is a list of command strings. They are executed in the order they are provided. This cannot be provided with script or scripts.

script - This is a path (relative or absolute) to a local script that will be copied to the remote resource and then executed. This cannot be provided with inline or scripts.

scripts - This is a list of paths (relative or absolute) to local scripts that will be copied to the remote resource and then executed. They are executed in the order they are provided. This cannot be provided with inline or script.

https://www.terraform.io/docs/language/resources/provisioners/remote-exec.html

<h2>What does the coalesce built-in function in Terraform do?</h2>

<h3>Answer</h3>
coalesce takes any number of arguments and returns the first one that isn't null or an empty string.

<h3>Explanation</h3>
coalesce https://www.terraform.io/docs/language/functions/coalesce.html

<h2>When running terraform init, it will do the following:</h2>

<h3>Answer</h3>
Create a dependency lock file, Download plugin dependencies https://www.terraform.io/docs/cli/commands/init.html, Create a .terraform directory

<h2>How does Terraform Cloud backup states?</h2>

<h3>Answer</h3>

Terraform Cloud saves a history of state files every time you perform a run

https://www.terraform.io/docs/language/state/index.html

<h2>When defining a data source block, how can we narrow down the resource we want to select from a remote provider?</h2>

<h3>Answer</h3>
The filter block allows a data source to select resources from a provider.

```json
data "aws_ami" "web" {
  filter {
    name   = "state"
    values = ["available"]
  }

  filter {
    name   = "tag:Component"
    values = ["web"]
  }
}
```
https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/subnet_ids#argument-reference

<h2>When specifying a module from an Arbitrary Git repository the following protocols are allowed</h2>

<h3>Answer</h3>
SSH and HTTPS

<h3>Explanation</h3>
https://www.terraform.io/docs/language/modules/sources.html#generic-git-repository

Arbitrary Git repositories can be used by prefixing the address with the special git:: prefix. After this prefix, any valid Git URL can be specified to select one of the protocols supported by Git.

For example, to use HTTPS or SSH:

module "vpc" { source = "git::https://example.com/vpc.git" }

module "storage" { source = "git::ssh://username@example.com/storage.git" }

<h2>Which Terraform Workflow ( Write -> Plan -> Create ) does this describe?</h2>

The project resides in a repo, and the backend is configured to use Terraform Cloud
Pull requests are submitted to the repo with new changes
When the Pull Request is approved Terraform Cloud runs terraform apply

<h3>Answer</h3>
Core Workflow Enhanced
  <a target="_blank" href="https://www.terraform.io/intro/core-workflow#the-core-workflow-enhanced-by-terraform-cloud">The Core Workflow Enhanced by Terraform Cloud</a>
  
<h2>The safest place to store your state file is within your git repository</h2>

<h3>Answer</h3>
False

<h3>Explanation</h3>
Your state file can contain sensitive information, and storing in your codebase git repository is considered dangerous.

<h2>The Terraform Registry contains both public and private providers and modules</h2>

<h3>Answer</h3>
False

<h3>Explanation</h3>
The Terraform Registry only contains public providers and modules.

https://www.terraform.io/docs/registry/private.html

<h2>When using terraform apply -replace= you can only specify a single resource for replacement</h2>
  
<h3>Answer</h3>
True

<h3>Explanation</h3>
This is true, you can only replace a single resource at a time.

https://www.terraform.io/docs/cli/commands/taint.html

For example,

terraform apply -replace="aws_instance.example[0]"

<h2>When we want the most verbose information from terraform logging what severity should we set?</h2>

<h3>Answer</h3>
TRACE

<h3>Explanation</h3>
https://www.terraform.io/docs/internals/debugging.html

You can set TF_LOG to one of the log levels TRACE, DEBUG, INFO, WARN, or ERROR to change the verbosity of the logs.

https://stackoverflow.com/questions/2031163/when-to-use-the-different-log-levels

Trace - Only when I would be "tracing" the code and trying to find one part of a function specifically. Debug - Information that is diagnostically helpful to people more than just developers (IT, sysadmins, etc.).
Info - Generally useful information to log (service start/stop, configuration assumptions, etc). Info I want to always have available but usually don't care about under normal circumstances. This is my out-of-the-box config level.
Warn - Anything that can potentially cause application oddities, but for which I am automatically recovering. (Such as switching from a primary to backup server, retrying an operation, missing secondary data, etc.)
Error - Any error which is fatal to the operation, but not the service or application (can't open a required file, missing data, etc.). These errors will force user (administrator, or direct user) intervention. These are usually reserved (in my apps) for incorrect connection strings, missing services, etc.

<h2>How do Terraform backups work when using a local backend?</h2>

<h3>Answer</h3>	
Terraform takes the current state and stores it in a file called terrraform.tfstate.backup

<h3>Explanation</h3>
Its not easy to find documentation for this feature, but if you test in practice you will see that this is how it works locally.

<h2>Which Terraform Workflow ( Write -> Plan -> Create ) does this describe?

The project resides in a repo, and the backend is configured to use Terraform Cloud
Pull requests are submitted to the repo with new changes
When the Pull Request is approved Terraform Cloud runs terraform apply</h2>

<h3>Answer</h3>	
Core Workflow Enhanced

<h3>Explanation</h3>
The Core Workflow Enhanced by Terraform Cloud

