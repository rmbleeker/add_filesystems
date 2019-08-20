Role Name
=========

This role adds partitions, volume groups and logical volumes to a machine.

Requirements
------------

There are no additional requirements.

Role Variables
--------------

The following dictionaries are used by this role:

# disks
#   - device
#     label (optional)
#     partitions
#       - number
#         name (required for GPT labeled partitions, defaults to the partition type "primary" if not used)
#         flags (optional)
#         start (optional)
#         end (optional)
#         fstype (do not define when using lvm)
#         mount_point (do not define when using lvm)
#         mount_options (optional)
#           - list of mount options
#   - device
#     ...

# vg
#   - name
#     devices
#       - list of block devices
#     lv
#       - name
#         size
#         fstype
#         mount_point
#         mount_options (optional)
#           - list of mount options
#   - name
#     ...

If you do not want raw disks in your volume group (e.g. "vg.devices: /dev/sdb" instead of "vg.devices: /dev/sdb1"), specify
at least the disk device. Parted will automatically create a single primary partition on that device using its full size.

Example:

#disks:
#  - device: /dev/sdb

Dependencies
------------

None.

License
-------

BSD

Author Information
------------------

ruud.bleeker@identiteitendiensten.nl

