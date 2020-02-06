# How to create linux swap file

Swap is a space on a disk that is used when the amount of physical RAM memory is full. When a Linux system runs out of RAM, inactive pages are moved from the RAM to the swap space.

Swap space can take the form of either a dedicated swap partition or a swap file. In most cases when running Linux on a virtual machine a swap partition is not present so our only option is to create a swap file.

Follow these steps to add 1GB of swap to your server. If you want to add 2GB instead of 1 GB, replace 1G with 2G.

<br>
<br>

#### 1. Create a file which will be used for swap.

    $sudo fallocate -l 1G /swapfile

If faillocate is not installed or if you get an error message saying fallocate failed: Operation not supported then you can use the following command to create the swap file:

    $sudo dd if=/dev/zero of=/swapfile bs=1k count=2048k

#### 2. Set the correct permissions.

Only the root user should be able to write and read the swap file. To set the correct permissions type:

    $sudo chmod 600 /swapfile

#### 3. Set up a Linux swap area.

Use the mkswap utility to set up the file as Linux swap area:

    $sudo mkswap /swapfile

#### 4. Enable the swap.

Activate the swap file with the following command:

    $sudo swapon /swapfile

**(Optional)** If you want the change to be permanent open the /etc/fstab file and append the following line:

    /swapfile swap swap defaults 0 0

#### 5. Verify the swap status.

To verify that the swap is active we can use either the swapon or the free command as shown below:

    sudo swapon --show

    NAME      TYPE SIZE  USED     PRIO
    /swapfile file 1024M 507.4M   -1

    $sudo free -h
                total        used      free    shared  buff/cache   available
    Mem:        488M         158M      83M     2.3M    246M         217M
    Swap:       1.0G         506M      517M

**And now you have successfully created a swap file for your system.**
<br>
<br>

## Adjust swappiness value

Swappiness is a Linux kernel property that defines how often the system will use the swap space. Swappiness can have a value between 0 and 100. A low value will make the kernel to try to avoid swapping whenever possible while a higher value will make the kernel to use the swap space more aggressively.

The default swappiness value is 60. You can check the current swappiness value by typing the following command:

    $sudo sysctl vm.swappiness=10

**(Optional)** To make this parameter persistent across reboots append the following line to the /etc/sysctl.conf file:

    vm.swappiness=10

The optimal swappiness value depends on your system workload and how the memory is being used. You should adjust this parameter in small increments to find an optimal value.

## Remove Swap File

If for any reason you want to deactivate and remove the swap file, follow these steps:

#### 1. First, deactivate the swap by typing:

    $sudo swapoff -v /swapfile

#### 2. If swap file entry is added to fstab then remove the swap file entry /swapfile swap swap defaults 0 0 from the /etc/fstab file.

#### 3. Finally delete the actual swapfile file using the rm command:

    $sudo rm /swapfile

## Conclusion

You have learned how to create a swap file and activate and configure swap space on your Linux system.
