---
title: "NFS Server: A Complete Guide to Setting Up and Configuring"
dateString: Dec 2022
# weight: 1

tags: ["Practical Devops"]

# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: true
draft: false
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: true
searchHidden: true
ShowReadingTime: false
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: false
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---
    
    
# Introduction    
Are you looking for a way to share files between multiple machines in a network? NFS (Network File System) may be just what you need! In this guide, we'll walk you through the process of setting up and configuring an NFS server on Linux.

# Step 1: Install the Required Packages
The first step is to install the required packages on your server. You can do this by running the following command:
    
    sudo apt-get install nfs-kernel-server
    
    
# Step 2: Create the Export Directory
Next, create a directory that you want to share with the client machines. In this example, we'll use `/var/nfs/share` as the export directory. Run the following command to create it:



    sudo mkdir -p /var/nfs/share
# Step 3: Configure the NFS Exports File
The NFS exports file determines which directories are shared with the client machines. Open the file /etc/exports with your favorite text editor and add the following line:



    /var/nfs/share 192.168.0.0/24(rw,sync,no_subtree_check)
This line allows machines on the 192.168.0.0/24 network to read and write to the `/var/nfs/share` directory. The `rw` option allows read and write access, the `sync` option ensures changes are immediately written to the disk, and the `no_subtree_check` option disables subtree checking.

# Step 4: Restart the NFS Server
After making changes to the exports file, you need to restart the NFS server for them to take effect. Run the following command:


    sudo systemctl restart nfs-kernel-server
# Step 5: Configure the Firewall
By default, NFS uses TCP port 2049 for communication. If you're using a firewall, you'll need to open this port. Run the following command to open the port using UFW:

```
sudo ufw allow from 192.168.0.0/24 to any port nfs
```
# Step 6: Mount the NFS Share on the Client Machine
Finally, you can mount the NFS share on the client machine. Run the following command:


    sudo mount 192.168.0.10:/var/nfs/share /mnt
This command mounts the `/var/nfs/share` directory on the NFS server at IP address `192.168.0.10` to the `/mnt` directory on the client machine.

# Conclusion
Setting up an NFS server may seem daunting at first, but it's actually a fairly simple process. By following the steps outlined in this guide, you should be able to configure an NFS server and share files with client machines in no time. Good luck!    

    
    
