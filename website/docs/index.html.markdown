---
layout: "template"
page_title: "Provider: Template"
sidebar_current: "docs-template-index"
description: |-
  The Template provider is used to template strings for other Terraform resources.
---

# Template Provider

This is a fork of the archived [hashicorp/template](https://registry.terraform.io/providers/hashicorp/template) provider.
This fork exists for two reasons:

- There is no arm64 build of the archived provider available
- There is currently no built-in 'templatestring' function to work with inline template strings/variables

If you only need to work with files (rather than strings/variables), you should use [the `templatefile` function](/docs/configuration/functions/templatefile.html) instead, which can be used directly in expressions without creating a separate data resource.

## Example Usage

```hcl
# Template for initial configuration bash script
data "template_file" "init" {
  template = "${file("init.tpl")}"
  vars = {
    consul_address = "${aws_instance.consul.private_ip}"
  }
}

# Create a web server
resource "aws_instance" "web" {
  # ...

  user_data = "${data.template_file.init.rendered}"
}
```
