---
title: "Hello World"
output: pdf_document
---

### Resize the Swap Partition on Linux

To resize the swap partition in Linux (Pop!_OS or another distribution), follow these steps carefully. It's important to back up any critical data before proceeding, as improper changes may lead to data loss or system instability.

#### 1. Disable the Swap Space
Before resizing the swap, you need to disable it temporarily. Run the following command to turn off the current swap:

```bash
sudo swapoff -a
```

#### 2. Modify the Swap Size

There are two possibilities: your swap space is either a file or a dedicated partition.

##### A. If Swap is a File

1. **Remove the old swap file:**
Assuming the swap file is located at `/mnt/[n]G.swap`, where n is a size of your swap. You can delete it with:

```bash 
sudo rm /mnt/[n]G.swap
```

2. **Create a new swap file:**
For example to create an 8 GB swap file, use the following command:

```bash
sudo dd if=/dev/zero of=/mnt/8G.swap bs=1G count=8

```

3. **Configure the new swap file:**
```bash 
sudo chmod 600 /mnt/8G.swap
sudo mkswap /mnt/8G.swap
```

4. **Activate the new swap file**
```bash
sudo swapon /mnt/8G.swap
```


5. **Check if the new swap is activated**
```bash 
sudo swapon --show
```

6. **Update the** `/etc/fstab` **file:**

Add or modify the following line in /etc/fstab to ensure the swap file is activated at boot:

```bash
/mnt/8G.swap swap swap defaults 0 0
```





