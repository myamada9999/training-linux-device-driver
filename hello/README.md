
Setup
-----

Environment: Debian 8(jessie) amd64
 
 $ sudo aptitude install linux-headers-3.16.0-4-amd64

Build
-----

 $ make

Load driver
-----------

 $ sudo insmod hello

 $ dmesg | tail

...
[ 5251.021110] driver loaded
[ 5251.021125] Hello world

 $ lsmod | head

Module                  Size  Used by
hello                  12458  0 

Unload driver
-------------

 $ sudo rmmod hello

 $ dmesg | tail

[   71.113037] ip_tables: (C) 2000-2006 Netfilter Core Team
[  123.976423] e1000: eth0 NIC Link is Down
[  125.991237] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  268.804831] UDF-fs: warning (device sr0): udf_fill_super: No partition found (2)
[  268.817129] ISO 9660 Extensions: Microsoft Joliet Level 3
[  269.159552] ISO 9660 Extensions: RRIP_1991A
[  273.402670] traps: tracker-extract[1457] trap int3 ip:7f4432763d30 sp:7ffef1b96670 error:0
[ 5251.021110] driver loaded
[ 5251.021125] Hello world
[ 5275.692672] driver unloaded

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

