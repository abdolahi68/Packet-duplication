This code the code to create duplicate packets for UDP and ICMP packets on linux kernel.

To install:
1.Download ubuntu 22.04 with Kernel 5.15.0.

2. Put the files in /net/ipv4/ directoy
3. The packet will send over the defualt interface. So, it is essenatil to set the name and IP address in the following functions:
   - udp.c: static int udp_send_skb(struct sk_buff *skb, struct flowi4 *fl4, struct inet_cork *cork) ---improve ---> if (iph->saddr == in_aton("192.168.1.242") &&  iph->daddr == in_aton("239.0.0.1")) 

   - ICMP: dev = dev_get_by_name(&init_net, "wlp2s2"); and  iph->daddr = in_aton("The IP of Second Interface");
   
5. use the following commands to compile the kernel:
   
  * make -j$(nproc)
  * make modules
  * make modules_install
  * make install
  * update-grub




