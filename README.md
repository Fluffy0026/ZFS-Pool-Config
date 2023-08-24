# file-server
## _**1. Installing ZFS**_
```sudo apt install zfsutils-linux```

## _**3. Creating a ZFS Pool**_
Choosing Drives to Pool

```sudo fdisk -l```

```ls -l /dev/disk/by-id/```
### Creating a Pool

There are two types of simple storage pools we can create. A striped pool , also called RAID-0 , in which the data is stored in “stripes” across all drives, or a mirrored pool , also called RAID-1 , in which a complete copy of all data is stored separately on each drive. Striped pools are not fault tolerant whereas mirrored pools can survive the failure of one drive. Striped pools have twice the storage capacity of mirrored pools and have better performance than mirrored pools.
To create a striped pool, we run:

```
When making pool use the ATA identifier not /dev/sda or anything else
Example:
ata-INTEL_####A2#160G##C_################## -> ../../sdb
```


```sudo zpool create myzpool mirror ata-INTEL_####A2#160G##C_################## ata-INTEL_####A2#160G##C_##################```

```sudo zfs set compression=lz4 mypool```
```sudo zfs set atime=off myzpool```

Add Cache Drive
```sudo zpool add myzpool cache 'ssd device name'```


