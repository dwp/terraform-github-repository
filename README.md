# GitHub Repository Terraform Module
Terraform module to manage GitHub repositories

## Requirements
- Terraform 0.14
- GitHub personal access token with the following permissions:
    - `admin:repo_hook, delete_repo, read:org, read:user, repo`
- A GitHub organisation or user

## Usage
### For a GitHub organisation
```hcl
module "my_repo" {
  source = "dwp/repository/github"
  name   = "my-repo"
}
```
### For a GitHub user
```hcl
module "my_repo" {
  source                    = "dwp/repository/github"
  name                      = "my-repo"
  branch_protection_enabled = false
}
```

## Example
```hcl
variable "github_organization" {
  type        = string
  description = "GitHub Organisation to create repos in"
  default     = "dwp"
}

variable "github_token" {
  type        = string
  description = "GitHub personal access token for managing repos"
}

provider "github" {
  token        = var.github_token
  organization = var.github_organization
}

resource "github_team" "a_team" {
  name    = "A-Team"
  privacy = "closed"
}

module "my_repo" {
  source      = "dwp/repository/github"
  name        = "my-repo"
  description = "My repo that demonstrates how to use this module"

  template = {
    owner = "my-org"
    repo  = "my-template-repo"
  }

  team_access = {
    my_team = {
      team_id = github_team.integration.id
      access = "push"
    }
  }
}
```
