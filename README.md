**This repository is an unofficial fork**

---

Terraform Provider
==================

Usage
-----

```hcl
terraform {
  required_providers {
    mysql = {
      source  = "kaplanmaxe/mysql"
      version = "1.9.4"
    }
  }
  required_version = ">= 0.13"
}

provider "mysql" {
}
```
Multiple create databases
-----
}
```
provider "mysql" {
  endpoint = "${aws_db_instance.MySQL[count.index].endpoint}"
  username = "${aws_db_instance.MySQL[count.index].username}"
  password = "${aws_db_instance.MySQL[count.index].password}"
}

resource "mysql_database" "databases" {
  count = length(var.database)
  name  = var.database[count.index]
}
```
In variables.tf :
```
variable "database" {
  type = list(string)
}
```
In *.tfvars : 

```
database      = ["auth", "ifms_burt"]

```
