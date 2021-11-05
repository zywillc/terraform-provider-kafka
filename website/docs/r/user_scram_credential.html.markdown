---
layout: "kafka"
page_title: "Kafka: kafka_user_scram_credential"
sidebar_current: "docs-kafka-resource-user-scram-credential"
description: |-
  A resource for managing Kafka User Scram Credentials.
---

# Resource: kafka_user_scram_credential

A resource for managing Kafka User Scram Credentials.
>**REQUIREMENT**:
Kafka version >= 2.7.0
## Example Usage

```hcl
provider "kafka" {
  bootstrap_servers = ["localhost:9092"]
  ca_cert      = file("../secrets/ca.crt")
  client_cert  = file("../secrets/terraform-cert.pem")
  client_key   = file("../secrets/terraform.pem")
  skip_tls_verify   = true
}

resource "kafka_user_scram_credential" "test" {
  username              = "test"
  scram_mechanism       = "SCRAM-SHA-512"
  scram_iterations      = 4096
  password              = var.password
}
```

## Argument Reference

The following arguments are supported:

* `username` - (Required) The name of the user.
* `scram_mechanism` - (Optional) The type of scram mechanism. Valid values are `SCRAM-SHA-256`,
  `SCRAM-SHA-512`. **Default** is `SCRAM-SHA-512`
* `scram_iterations` - (Optional) The iterations for scram mechanism. Valid values at at least 4096. **Default** is `4096`
* `password` - (Required) The credential of the user. can be referenced to a Environment Variable.
