---
layout: "kafka"
page_title: "Kafka: kafka_quota"
sidebar_current: "docs-kafka-resource-quota"
description: |-
  A resource for managing Kafka quotas.
---

# Resource: kafka_quota

A resource for managing Kafka quotas.

## Example Usage

```hcl
provider "kafka" {
  bootstrap_servers = ["localhost:9092"]
  ca_cert           = file("../secrets/ca.crt")
  client_cert       = file("../secrets/terraform-cert.pem")
  client_key        = file("../secrets/terraform.pem")
}

resource "kafka_quota" "test" {
  entity_name       = "client1"
  entity_type       = "client-id"
  config = {
    "consumer_byte_rate" = "4000000"
    "producer_byte_rate" = "3500000"
  }
}
```

## Argument Reference

The following arguments are supported:

* `entity_name` - (Required) The name of the entity.
* `entity_type` - (Required) The entity type (client-id, user, ip).
* `config` - (Required) A map of string attributes for the entity
