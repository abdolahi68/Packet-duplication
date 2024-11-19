# Duplicate Packet Generator for UDP and ICMP on Linux Kernel

## Overview

This repository contains code to create duplicate packets for UDP and ICMP protocols within the Linux kernel. The modified kernel code sends duplicate packets over a specified interface.

## Prerequisites

- **Operating System:** Ubuntu 22.04
- **Kernel Version:** 5.15.0

## Installation Instructions

### 1. Install the Required Kernel Version

Ensure you have the correct kernel version installed:


```bash
sudo apt install linux-image-5.15.0-50-generic
```
###  2. Place the Modified Files
Copy the modified source files (udp.c, ping.c, etc.) into the kernel source directory:
```
<kernel_source_directory>/net/ipv4/
```
### 3. Configure Interface Names and IP Addresses
The code sends packets over the default interface. Update the interface names and IP addresses in the following files:

-  In udp.c:

```bash
static int udp_send_skb(struct sk_buff *skb, struct flowi4 *fl4, struct inet_cork *cork)
```

Modify the condition to match your second interface IP and the multicast IP for the duplicate packet:

```bash
if (iph->saddr == in_aton("SECOND_INTERFACE_IP") && iph->daddr == in_aton("MULTICAST_IP_FOR_DUPLICATE"))
```

- In ping.c:

Set the device name and destination IP address:

```bash
dev = dev_get_by_name(&init_net, "INTERFACE_NAME");
iph->daddr = in_aton("SECOND_INTERFACE_IP");
```

Note: Replace the placeholders with your actual network configurations:

```SECOND_INTERFACE_IP:``` The IP address of your second interface.

```MULTICAST_IP_FOR_DUPLICATE:``` The multicast IP for the duplicate packet.

```INTERFACE_NAME:``` The name of your network interface (e.g., eth1, wlp2s2).

### 4. Compile the Kernel
```bash
make -j$(nproc)
sudo make modules_install
sudo make install
sudo update-grub
sudo reboot
```


