Terraform Provider
==================

This is a fork of the archived [hashicorp/template](https://registry.terraform.io/providers/hashicorp/template) provider.
This fork exists for two reasons:

- There is no arm64 build of the archived provider available
- There is currently no built-in 'templatestring' function

Requirements
------------

-	[Terraform](https://www.terraform.io/downloads.html) 0.10.x
-	[Go](https://golang.org/doc/install) 1.11 (to build the provider plugin)

Usage
---------------------

To make the provider available for use in your module, you must first declare
it as a required provider inside your `terraform` block:

```hcl
terraform {
  required_providers {
    template = {
      source = "lewispeckover/template"
      version = "~> 2.2.1"
    }
  }
}
```

Building The Provider
---------------------

Clone repository to: `$GOPATH/src/github.com/terraform-providers/terraform-provider-template`

```sh
$ mkdir -p $GOPATH/src/github.com/terraform-providers; cd $GOPATH/src/github.com/terraform-providers
$ git clone git@github.com:terraform-providers/terraform-provider-template
```

Enter the provider directory and build the provider

```sh
$ cd $GOPATH/src/github.com/terraform-providers/terraform-provider-template
$ make build
```

Using the provider
----------------------
## Fill in for each provider

Developing the Provider
---------------------------

If you wish to work on the provider, you'll first need [Go](http://www.golang.org) installed on your machine (version 1.11+ is *required*). You'll also need to correctly setup a [GOPATH](http://golang.org/doc/code.html#GOPATH), as well as adding `$GOPATH/bin` to your `$PATH`.

To compile the provider, run `make build`. This will build the provider and put the provider binary in the `$GOPATH/bin` directory.

```sh
$ make build
...
$ $GOPATH/bin/terraform-provider-template
...
```

In order to test the provider, you can simply run `make test`.

```sh
$ make test
```

In order to run the full suite of Acceptance tests, run `make testacc`.

*Note:* Acceptance tests create real resources, and often cost money to run.

```sh
$ make testacc
```
