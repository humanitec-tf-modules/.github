# Terraform/OpenTofu (TF) modules for the Platform Orchestrator

This GitHub organization contains repositories providing curated Terraform/OpenTofu ("TF") modules for use with the [Humanitec Platform Orchestrator](https://developer.humanitec.com/platform-orchestrator).

There are two kinds of module repositories: [Orchestrator configuration modules](#orchestrator-configuration-modules) and [Resource Definition sources](#resource-definition-sources).

## Orchestrator configuration modules

Orchestrator configuration modules are for creating Orchestrator configuration objects like runner clusters, Cloud Accounts, Secret Stores etc. using the `humanitec/humanitec` TF provider. They may also be able to create 3rd party objects like e.g. cloud infrastructure supporting the Orchestrator objects. Refer to each module repository `README` for details.

Use these modules in your TF code like this:

```terraform
terraform {
  required_providers {
    platform-orchestrator = {
      source  = "humanitec/humanitec"
      version = "~> 1"
    }
  }
}

module "orchestrator_setup" {
  source = "github.com/humanitec-tf-modules/some-tf-module?ref=v1.2.3" # Use ref to pin a version

  some_param = ... # Provide module parameters

}
```

Orchestrator configuration modules are prefixed `orchestrator-` and suffixed with the main type of Orchestrator object they provide, e.g. `orchestrator-cloud-account-aws`.

## Resource Definition sources

Resource Definition sources are used as the `source` in Platform Orchestrator [Resource Definitions](https://developer.humanitec.com/platform-orchestrator/docs/platform-orchestrator/resources/resource-definitions/) where applicable. For example, the [Terraform and OpenTofu Container](https://developer.humanitec.com/platform-orchestrator/docs/integration-and-extensions/drivers/terraform-and-opentofu-container-builtin/) Driver lets you specify an external source to download IaC code.

Orchestrator module sources never create any Orchestrator objects using the `humanitec/humanitec` TF provider, but only third party objects using other provider(s).

## Usage

Refer to each individual repository for usage instructions including full parameterization options.

## Contributing

You need to be a member of this GitHub organization to create new module repositories. Go to the [Members README](https://github.com/humanitec-tf-modules?view_as=member) for details (accessible for organization members only).