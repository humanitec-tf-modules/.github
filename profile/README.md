# Terraform/OpenTofu (TF) modules for the Humanitec Platform Orchestrator

This GitHub organization contains repositories providing curated Terraform/OpenTofu ("TF") modules for use with the [Humanitec Platform Orchestrator](https://developer.humanitec.com/platform-orchestrator).

There are two kinds of module repositories: [Orchestrator configuration modules](#orchestrator-configuration-modules) and [Orchestrator module sources](#orchestrator-module-sources).

## Orchestrator configuration modules

Orchestrator configuration modules are for creating Orchestrator [configuration objects](https://developer.humanitec.com/platform-orchestrator/docs/configure/overview/) like runners, modules, projects etc. using the `humanitec/platform-orchestrator` TF provider. They may also be able to create 3rd party objects like e.g. cloud infrastructure supporting the Orchestrator objects. Refer to each module repository `README` for details.

Use these modules in your TF code like this:

```terraform
terraform {
  required_providers {
    platform-orchestrator = {
      source  = "humanitec/platform-orchestrator"
      version = "~> 2"
    }
  }
}

module "ecs_runner" {
  source = "github.com/humanitec-tf-modules/serverless-ecs-orchestrator-runner?ref=v1.2.3" # Use ref to pin a version

  some_param = ... # Provide module parameters

}
```

Orchestrator configuration modules are suffixed with the main type of Orchestrator object they provide, e.g. `-runner`.

## Orchestrator module sources

Orchestrator module sources are used as the `module_source` in Platform Orchestrator [modules](https://developer.humanitec.com/platform-orchestrator/docs/configure/modules/overview/). As an Orchestrator user, you will not usually use these modules yourself, rather they will be used by the [Orchestrator configuration modules](#orchestrator-configuration-modules).

Orchestrator module sources never create any Orchestrator objects using the `humanitec/platform-orchestrator` TF provider, but only third party objects using other provider(s).

## Contributing

You need to be a member of this GitHub organization to create new module repositories. Go to the [Members README](https://github.com/humanitec-tf-modules?view_as=member) for details (accessible for organization members only).
