This code is create duplicate packets for UDP and ICMP packets on linux kernel.

To install:
1.Download ubuntu 22.04 with Kernel 5.15.0.
2. Put the files in /net/ipv4/ directoy
3. use the following commands to compile the kernel:
  * make -j$(nproc)
  * make modules
  * make modules_install
  * make install
  * update-grub


