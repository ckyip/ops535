# Scripts Written for OPS535 / SPR500

Professor : Raymond Chan

By Student: Colin Yip

###Scenario:

A Image which serves as a base image (clone source) for assignment and lab is provided.  A URL of the file is given. 
Following scripts has been written to automate setting up the VM.

###Files:

####vm_downloader: Automate downloading and updating of a provided base image (pre-cloning prep)
####vm_cloner    : Make copies of a given base image file (.qcow2) and attach each to a VM

# vm_downloader

Input:
URL of assignment/lab base image (.qcow2 / .gz)

Output:
Updated base image (.qcow2) in /var/lib/libvirt/images

Usage Example:

./vm_downloader https://scs.senecac.on.ca/~raymond.chan/ops535/asgms/c7min-ops535.qcow2.gz 

Description:

This script does the following:

1. Download VM image / md5sum files from URL
2. Automatic decompress, check md5sum, move file to /var/lib/libvirt/images
3. (Optional) Automate yum update by mounting image to a temporary VM
4. Remove temporary VM

# vm_cloner

Launches a User Interface written using "whiptail".

Usage Example:
./vm_cloner

Description:

This script does the following:

1. Ask the user to choose a base image (.qcow2) from /var/lib/libvirt/images
2. Ask the user to choose the VM to be created off the image
3. Ask the user choose virtual network the cloned VM should have interface on
4. Create the VM with above settings