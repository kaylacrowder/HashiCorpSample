# Getting Started with Terraform

Terraform is a popular infrastructure as code (IaC) tool that uses configuration language to provision infrastructure. It has many providers, from public clouds to PaaS and SaaS APIs. [View the provider registry here.](https://registry.terraform.io/browse/providers)

This guide uses Terraform to create an NGINX web server Docker container on your local machine.

## Prerequisites

* Install Terraform
* Install Docker [Docker Installation Instructions](https://docs.docker.com/engine/install/)
* Start Docker Engine

## NGINX Docker Terraform Tutorial

To install Terraform, visit [Terraform.io](https://www.terraform.io/downloads.html). Here you will find the instructions for your specific local environment.

Verify the installation by running Terraform's help command.
```shell
$ terraform --help
```

Your output should be similar to the text below and include a list of commands.

```shell
$ terraform --help
Usage: terraform [global options] <subcommand> [args]

The available commands for execution are listed below.
The primary workflow commands are given first, followed by
less common or more advanced commands.
```

Create a new directory on your local machine.

```shell
$ mkdir terraform-demo
$ cd terraform-demo
```
Create a file for your Terraform configuration code.

```shell
$ touch main.tf
```
Open the file in your editor and paste the following lines.

This Terraform script creates a local NGINX Docker container using the latest version from NGINX on the Docker registry. [Link to Docker Image](https://hub.docker.com/_/nginx)

See this documentation for details about remote Docker Hosts or other installation types: [Terraform Docker Provider](https://registry.terraform.io/providers/kreuzwerker/docker/latest/docs)

```hcl
terraform {
  required_providers {
    docker = {
      source = "kreuzwerker/docker"
    }
  }
}

provider "docker" {
    host = "unix:///var/run/docker.sock"
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "sampleKMC"
  ports {
    internal = 80
    external = 8000
  }

}
resource "docker_image" "nginx" {
  name = "nginx:latest"
  keep_locally = false
}
```

Initialize Terraform with the `init` command.

```shell
$ terraform init
```

This command initializes the provider and downloads any required packages.

```shell
Initializing the backend...

Initializing provider plugins...
- Finding latest version of kreuzwerker/docker...
- Installing kreuzwerker/docker v3.0.2...
- Installed kreuzwerker/docker v3.0.2 (self-signed, key ID BD080C4571C6104C)

Partner and community providers are signed by their developers.
If you'd like to know more about provider signing, you can read about it here:
https://www.terraform.io/docs/cli/plugins/signing.html

Terraform has created a lock file .terraform.lock.hcl to record the provider
selections it made above. Include this file in your version control repository
so that Terraform can guarantee to make the same selections by default when
you run "terraform init" in the future.

Terraform has been successfully initialized!

You may now begin working with Terraform. Try running "terraform plan" to see
any changes that are required for your infrastructure. All Terraform commands
should now work.

If you ever set or change modules or backend configuration for Terraform,
rerun this command to reinitialize your working directory. If you forget, other
commands will detect it and remind you to do so if necessary.
```

Run **terraform plan** to show the plan file. This is a list of all resources Terraform will create.

```shell
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create

Terraform will perform the following actions:

  # docker_container.nginx will be created
  + resource "docker_container" "nginx" {
      + attach                                      = false
      + bridge                                      = (known after apply)
      + command                                     = (known after apply)
      + container_logs                              = (known after apply)
      + container_read_refresh_timeout_milliseconds = 15000
      + entrypoint                                  = (known after apply)
      + env                                         = (known after apply)
      + exit_code                                   = (known after apply)
      + hostname                                    = (known after apply)
      + id                                          = (known after apply)
      + image                                       = (known after apply)
      + init                                        = (known after apply)
      + ipc_mode                                    = (known after apply)
      + log_driver                                  = (known after apply)
      + logs                                        = false
      + must_run                                    = true
      + name                                        = "sampleKMC"
      + network_data                                = (known after apply)
      + read_only                                   = false
      + remove_volumes                              = true
      + restart                                     = "no"
      + rm                                          = false
      + runtime                                     = (known after apply)
      + security_opts                               = (known after apply)
      + shm_size                                    = (known after apply)
      + start                                       = true
      + stdin_open                                  = false
      + stop_signal                                 = (known after apply)
      + stop_timeout                                = (known after apply)
      + tty                                         = false
      + wait                                        = false
      + wait_timeout                                = 60

      + ports {
          + external = 8000
          + internal = 80
          + ip       = "0.0.0.0"
          + protocol = "tcp"
        }
    }

  # docker_image.nginx will be created
  + resource "docker_image" "nginx" {
      + id           = (known after apply)
      + image_id     = (known after apply)
      + keep_locally = false
      + name         = "nginx:latest"
      + repo_digest  = (known after apply)
    }

Plan: 2 to add, 0 to change, 0 to destroy.

───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────

Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these actions if you
run "terraform apply" now.
```

If the plan file matches your expectation, run **terraform apply.**

```shell
$ terraform apply
```

The Terraform output should match your plan file. Type `yes` to create it.

```shell
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create

Terraform will perform the following actions:

  # docker_container.nginx will be created
  + resource "docker_container" "nginx" {
      + attach                                      = false
      + bridge                                      = (known after apply)
      + command                                     = (known after apply)
      + container_logs                              = (known after apply)
      + container_read_refresh_timeout_milliseconds = 15000
      + entrypoint                                  = (known after apply)
      + env                                         = (known after apply)
      + exit_code                                   = (known after apply)
      + hostname                                    = (known after apply)
      + id                                          = (known after apply)
      + image                                       = (known after apply)
      + init                                        = (known after apply)
      + ipc_mode                                    = (known after apply)
      + log_driver                                  = (known after apply)
      + logs                                        = false
      + must_run                                    = true
      + name                                        = "sampleKMC"
      + network_data                                = (known after apply)
      + read_only                                   = false
      + remove_volumes                              = true
      + restart                                     = "no"
      + rm                                          = false
      + runtime                                     = (known after apply)
      + security_opts                               = (known after apply)
      + shm_size                                    = (known after apply)
      + start                                       = true
      + stdin_open                                  = false
      + stop_signal                                 = (known after apply)
      + stop_timeout                                = (known after apply)
      + tty                                         = false
      + wait                                        = false
      + wait_timeout                                = 60

      + ports {
          + external = 8000
          + internal = 80
          + ip       = "0.0.0.0"
          + protocol = "tcp"
        }
    }

  # docker_image.nginx will be created
  + resource "docker_image" "nginx" {
      + id           = (known after apply)
      + image_id     = (known after apply)
      + keep_locally = false
      + name         = "nginx:latest"
      + repo_digest  = (known after apply)
    }

Plan: 2 to add, 0 to change, 0 to destroy.

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes

docker_image.nginx: Creating...
docker_image.nginx: Creation complete after 10s [id=sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149eadnginx:latest]
docker_container.nginx: Creating...
docker_container.nginx: Creation complete after 0s [id=38f2cb3481bf0ae2d712b4a63eb59b5860a19cb914758a5103624de6409e4acc]


```
The apply command created your docker container.

Visit [http://localhost:8080](http://localhost:8080) to view the base NGINX installation.

![A screenshot of a web server welcome page on a white background that says "Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx."](https://github.com/kaylacrowder/HashiCorpSample/blob/main/education-engineer/localhost.jpg)

Run **docker ps** to verify the container is running.

```shell
$ docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                  NAMES
6582f4de6903   f71a4866129b   "/docker-entrypoint.…"   7 seconds ago   Up 6 seconds   0.0.0.0:8000->80/tcp   sampleKMC
```

Destroy the infrastructure when finished. You can run **terraform apply** again to recreate it.

Enter the command **terraform destroy**. Terraform outputs the destroy plan.
Type `yes` and hit ENTER. Terraform will destroy the resources.

```shell
$ terraform destroy
docker_image.nginx: Refreshing state... [id=sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149eadnginx:latest]
docker_container.nginx: Refreshing state... [id=6582f4de690349703bbfeb9019a632d72e9aaeda2da59ffd9ade078a4a30397d]

Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following
symbols:
  - destroy

Terraform will perform the following actions:

  # docker_container.nginx will be destroyed
  - resource "docker_container" "nginx" {
      - attach                                      = false -> null
      - command                                     = [
          - "nginx",
          - "-g",
          - "daemon off;",
        ] -> null
      - container_read_refresh_timeout_milliseconds = 15000 -> null
      - cpu_shares                                  = 0 -> null
      - dns                                         = [] -> null
      - dns_opts                                    = [] -> null
      - dns_search                                  = [] -> null
      - entrypoint                                  = [
          - "/docker-entrypoint.sh",
        ] -> null
      - env                                         = [] -> null
      - group_add                                   = [] -> null
      - hostname                                    = "6582f4de6903" -> null
      - id                                          = "6582f4de690349703bbfeb9019a632d72e9aaeda2da59ffd9ade078a4a30397d" -> null
      - image                                       = "sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149ead" -> null
      - init                                        = false -> null
      - ipc_mode                                    = "private" -> null
      - log_driver                                  = "json-file" -> null
      - log_opts                                    = {} -> null
      - logs                                        = false -> null
      - max_retry_count                             = 0 -> null
      - memory                                      = 0 -> null
      - memory_swap                                 = 0 -> null
      - must_run                                    = true -> null
      - name                                        = "sampleKMC" -> null
      - network_data                                = [
          - {
              - gateway                   = "172.17.0.1"
              - global_ipv6_address       = ""
              - global_ipv6_prefix_length = 0
              - ip_address                = "172.17.0.2"
              - ip_prefix_length          = 16
              - ipv6_gateway              = ""
              - mac_address               = "02:42:ac:11:00:02"
              - network_name              = "bridge"
            },
        ] -> null
      - network_mode                                = "default" -> null
      - privileged                                  = false -> null
      - publish_all_ports                           = false -> null
      - read_only                                   = false -> null
      - remove_volumes                              = true -> null
      - restart                                     = "no" -> null
      - rm                                          = false -> null
      - runtime                                     = "runc" -> null
      - security_opts                               = [] -> null
      - shm_size                                    = 64 -> null
      - start                                       = true -> null
      - stdin_open                                  = false -> null
      - stop_signal                                 = "SIGQUIT" -> null
      - stop_timeout                                = 0 -> null
      - storage_opts                                = {} -> null
      - sysctls                                     = {} -> null
      - tmpfs                                       = {} -> null
      - tty                                         = false -> null
      - wait                                        = false -> null
      - wait_timeout                                = 60 -> null

      - ports {
          - external = 8000 -> null
          - internal = 80 -> null
          - ip       = "0.0.0.0" -> null
          - protocol = "tcp" -> null
        }
    }

  # docker_image.nginx will be destroyed
  - resource "docker_image" "nginx" {
      - id           = "sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149eadnginx:latest" -> null
      - image_id     = "sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149ead" -> null
      - keep_locally = false -> null
      - name         = "nginx:latest" -> null
      - repo_digest  = "nginx@sha256:2ab30d6ac53580a6db8b657abf0f68d75360ff5cc1670a85acb5bd85ba1b19c0" -> null
    }

Plan: 0 to add, 0 to change, 2 to destroy.

Do you really want to destroy all resources?
  Terraform will destroy all your managed infrastructure, as shown above.
  There is no undo. Only 'yes' will be accepted to confirm.

  Enter a value: yes

docker_container.nginx: Destroying... [id=6582f4de690349703bbfeb9019a632d72e9aaeda2da59ffd9ade078a4a30397d]
docker_container.nginx: Destruction complete after 0s
docker_image.nginx: Destroying... [id=sha256:f71a4866129b6332cfd0dddb38f2fec26a5a125ebb0adde99fbaa4cb87149eadnginx:latest]
docker_image.nginx: Destruction complete after 1s

Destroy complete! Resources: 2 destroyed.
```

## Summary

In this tutorial, you created a Terraform configuration file, main.tf. You created a basic NGINX Docker container, viewed the main configuration page, and then destroyed the infrastructure.

## Next Up

To continue learning Terraform, create an EC2 instance with Terraform's AWS provider. [Terraform AWS Provider](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/aws-build)
