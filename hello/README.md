
Setup
-----

Test Environment: Debian 8(jessie) amd64
 
 $ sudo aptitude install linux-headers-3.16.0-4-amd64

Build
-----
 
 $ cd hello
 $ make

Load driver
-----------

 $ sudo insmod ./hello.ko 
 $ lsmod | head
 Module                  Size  Used by
 hello                  12458  0 
 nls_utf8               12456  1 
 isofs                  38965  1 
 udf                    87759  0 
 crc_itu_t              12347  1 udf
 xt_conntrack           12681  1 
 ipt_MASQUERADE         12594  1 
 iptable_nat            12646  1 
 nf_conntrack_ipv4      18448  2 
 $ dmesg | tail
 [  268.817129] ISO 9660 Extensions: Microsoft Joliet Level 3
 [  269.159552] ISO 9660 Extensions: RRIP_1991A
 [  273.402670] traps: tracker-extract[1457] trap int3 ip:7f4432763d30 sp:7ffef1b96670 error:0
 [ 5251.021110] driver loaded
 [ 5251.021125] Hello world
 [ 5275.692672] driver unloaded
 [ 6618.298826] e1000: eth0 NIC Link is Down
 [ 6620.301640] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
 [10196.947582] driver loaded
 [10196.947592] Hello world


Unload driver
-------------

 $ sudo rmmod hello
 $ dmesg | tail
 [  269.159552] ISO 9660 Extensions: RRIP_1991A
 [  273.402670] traps: tracker-extract[1457] trap int3 ip:7f4432763d30 sp:7ffef1b96670 error:0
 [ 5251.021110] driver loaded
 [ 5251.021125] Hello world
 [ 5275.692672] driver unloaded
 [ 6618.298826] e1000: eth0 NIC Link is Down
 [ 6620.301640] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
 [10196.947582] driver loaded
 [10196.947592] Hello world
 [10244.879070] driver unloaded

 $ lsmod | head
 Module                  Size  Used by
 nls_utf8               12456  1 
 isofs                  38965  1 
 udf                    87759  0 
 crc_itu_t              12347  1 udf
 xt_conntrack           12681  1 
 ipt_MASQUERADE         12594  1 
 iptable_nat            12646  1 
 nf_conntrack_ipv4      18448  2 
 nf_defrag_ipv4         12483  1 nf_conntrack_ipv4



