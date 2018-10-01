---
layout: "ovirt"
page_title: "oVirt: ovirt_disk"
sidebar_current: "docs-ovirt-resource-disk"
description: |-
  Manages a Disk resource within oVirt.
---

# ovirt\_disk

Manages a Disk resource within oVirt.

## Example Usage

```hcl
resource "ovirt_disk" "disk" {
  name              = "mydisk"
  alias             = "mydisk-alias"
  format            = "raw"
  quota_id          = "dbbd5819-efa9-4383-9aad-55330841ad3c"
  storage_domain_id = "fe98758d-60f8-4206-8ffc-f772e906d752"
  size              = 60
  shareable         = false
  sparse            = true
}
```

## Argument Reference

The following arguments are supported:

* `name` - (Required) A unique name for the disk. Changing this updates the disk's name.
* `alias` - (Optional) A alais for the disk. Changing this updates the disk's alias.
* `format` - (Required) The format of the disk. Valid valus are `cow` and `raw`. Changing this creates a new disk.
* `quota_id` - (Optional) The ID of quota applied to the disk. Changing this creates a new disk.
* `storage_domain_id` - (Required) The ID of storage domain the disk residents. Changing this creates a new disk.
* `size` - (Required) The size of the disk to create (in gigabytes). Changing this updates the disk's size and only the size extention is supported.
* `shareable` - (Optional) The flag to indicate whether the disk could be attached to multiple vms. Default is `false`. Changing this creates a new disk.
* `sparse` - (Optional) The flag to indicate whether the physical storage for the disk should not be preallocated. Changing this creates a new disk.

## Attributes Reference

The following attributes are exported:

* `name` - See Argument Reference above
* `alias` - See Argument Reference above
* `format` - See Argument Reference above
* `quota_id` - See Argument Reference above
* `storage_domain_id` - See Argument Reference above
* `size` - See Argument Reference above
* `shareable` - See Argument Reference above
* `sparse` - See Argument Reference above

## Import

Disks can be imported using the `id`, e.g.

```
$ terraform import ovirt_disk.disk 67f88160-396b-441b-8824-f2c22e80bf82
```