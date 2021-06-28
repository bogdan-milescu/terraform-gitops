# A GitOps approach to provision infrastructure in GCP with terraform

## Scope

This is meant to be a short PoC on how infrastructure can be provisioned on GCP with [Terraform](https://www.terraform.io/) in a automated manner, usign [GitOps principles](https://www.weave.works/blog/practical-guide-gitops) as an approach.

## Tools used

* [Terraform](https://www.terraform.io/) used to provision the resources
* [GitHub Actions](https://github.com/features/actions) used to automate the provision process

## Steps to prepare the environment

* Create a new GCP [project](https://cloud.google.com/resource-manager/docs/creating-managing-projects)

* Create a new user for Terrafor with edit right on the project and generate a key

* Add the gererated key as a secret in Repository --> Settings --> Secrets and call it *GOOGLE_CREDENTIALS*

* Create a bucket in GCP to be used as backend for Terraform tfstate file
```
gsutil mb -p BUCKET_NAME gs://BUCKET_NAME
```

* Enable versioning on the bucket

```
gsutil versioning set on gs://BUCKET_NAME
```

## Pipeline description