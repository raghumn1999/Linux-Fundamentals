# Disk and Storage Management in Linux

## Introduction to Disk and Storage Management
Managing disks and storage efficiently is crucial for system performance and stability. Linux provides 
various commands to monitor, partition, format, mount, and manage disk storage.

## Viewing Disk Information
### Using `lsblk`
List all block devices:
```bash
lsblk
```
### Using `fdisk`
View partition details:
```bash
fdisk -l
```
### Using `df`
Check available disk space:
```bash
df -h
```
### Using `du`
Find the size of a directory:
```bash
du -sh /var/log
```

## Partition Management
# Adding storage into linux system involvs the below steps.
* Create partition, this is block storage. In aws we can create EBS volume and attach EC2 instance,
  that will give new partition. we can store any content into block storage
* format the storage,we have two type of format, 1) ext4 and 2) xfs
* create directory where this storage need to mounted
  Ex: need 10GB in /apps,create /apps directory first.
* mount the formated storage into directory
   Ex: mount /dev/sdX1 /apps


### Creating a Partition with `fdisk`
```bash
fdisk /dev/sdX
```
Follow the interactive prompts to create a partition. sdX is name of partition,you can give whatever you 
want

### Formatting a Partition
Format as ext4:
```bash
mkfs -t ext4 /dev/sdX1
```
Format as XFS:
```bash
mkfs -t xfs /dev/sdX1
```

## Mounting and Unmounting
### Mount a Partition
```bash
mkdir /mnt/demo-volume
mount /dev/sdX1 /mnt/demo-volume
```
### Unmount a Partition
```bash
umount /mnt/demo-volume
```
### Remount a Partition
```bash
mount -o remount,rw /mnt/demo-volume
```

## LVM Management
### Create a Physical Volume
```bash
pvcreate /dev/sdX
```
### Create a Volume Group
```bash
vgcreate vg_name /dev/sdX
```
### Create a Logical Volume
```bash
lvcreate -L 10G -n lv_name vg_name
```
### Format and Mount the Logical Volume
```bash
mkfs.ext4 /dev/vg_name/lv_name
mount /dev/vg_name/lv_name /mnt
```

## Swap Management
### Create a Swap Partition
```bash
mkswap /dev/sdX
```
### Enable Swap
```bash
swapon /dev/sdX
```
### Disable Swap
```bash
swapoff /dev/sdX
```

