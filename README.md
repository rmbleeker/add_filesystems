# add_filesystems

This role adds partitions, volume groups and logical volumes to a machine.

### requirements

There are no additional requirements.

### role variables

The following dictionaries are used by this role:

```yaml
disks:
  - device: /dev/sda
    label: (optional)
    partitions:
      - number: 1
        name: (required for GPT labeled partitions, defaults to the partition type "primary" if not used)
        flags: (optional)
        start: (optional)
        end: (optional)
        fstype: (do not define when using lvm)
        mount_point: (do not define when using lvm)
        mount_options: (optional)
          - list of mount options
        owner: (optional, owner of the mount directory)
        group: (optional, group of the mount directory)
        mode: (optional, permissions of the mount directory)
  - device: /dev/sdb
    ...

vg:
  - name: vg_name
    devices:
      - list of block devices
    lv:
      - name: lv_name
        size:
        fstype:
        mount_point:
        mount_options: (optional)
          - list of mount options
  - name: vg_name
    ...
```

If you do not want raw disks in your volume group (e.g. "vg.devices: /dev/sdb" instead of "vg.devices: /dev/sdb1"), specify
at least the disk device. Parted will automatically create a single primary partition on that device using its full size.

Example:

```yaml
disks:
  - device: /dev/sdb
```

### dependencies

none

### license

BSD

### author information

ruud.bleeker@identiteitendiensten.nl
