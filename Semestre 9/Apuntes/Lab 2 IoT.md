

![[Pasted image 20260621130101.png]]

"id": 441356

![[Pasted image 20260621130132.png]]

[
    "m3-103.grenoble.iot-lab.info",
    "m3-104.grenoble.iot-lab.info",
    "m3-105.grenoble.iot-lab.info",
    "m3-106.grenoble.iot-lab.info"
]

![[Pasted image 20260621130153.png]]

Use CHANNEL=11, PAN_ID=0x18ca

![[Pasted image 20260621130218.png]]


![[Pasted image 20260621130327.png]]

![[Pasted image 20260621130319.png]]


## Actividad 1 

### 1.1 
1ra terminal

![[Pasted image 20260621130456.png]]


![[Pasted image 20260621130654.png]]

m3-103
inet6 addr: fe80::d8c0:5ba4:ed59:171f  scope: link  VAL

m3-104
inet6 addr: fe80::6c79:499f:b1bf:efbd  scope: link  VAL

![[Pasted image 20260621130806.png]]

ping fe80::6c79:499f:b1bf:efbd%6

![[Pasted image 20260621130938.png]]

ping fe80::6c79:499f:b1bf:efbd%6
12 bytes from fe80::6c79:499f:b1bf:efbd%6: icmp_seq=0 ttl=64 rssi=-45 dBm time=9.742 ms
12 bytes from fe80::6c79:499f:b1bf:efbd%6: icmp_seq=1 ttl=64 rssi=-45 dBm time=8.782 ms
12 bytes from fe80::6c79:499f:b1bf:efbd%6: icmp_seq=2 ttl=64 rssi=-45 dBm time=9.421 ms

--- fe80::6c79:499f:b1bf:efbd%6 PING statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 8.782/9.315/9.742 ms


### 1.2

![[Pasted image 20260621131227.png]]![[Pasted image 20260621131239.png]]

text	   data	    bss	    dec	    hex	filename
  80048	    144	  22188	 102380	  18fec	/home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router/bin/iotlab-m3/gnrc_border_router.elf
iotlab-node --jmespath='keys(@)[0]' --format='lambda ret: exit(int(ret))'  --list grenoble,m3,105 --flash /home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router/bin/iotlab-m3/gnrc_border_router.bin
make: Leaving directory '/home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router'

![[Pasted image 20260621132644.png]]

%%  sudo ethos_uhcpd.py m3-7 tap5 2001:660:5307:3120::1/64  %%

sudo ethos_uhcpd.py m3-106 tap5 2a00:1450:4007:80f::2003/64

![[Pasted image 20260621133029.png]]

|       |                    |                    |     |
| ----- | ------------------ | ------------------ | --- |
| Lille | 2001:660:4403:0480 | 2001:660:4403:04ff | 128 |

---
munozbar@grenoble:~$ ip addr show | grep tap
537: tap0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
9692: tap1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000

munozbar@grenoble:~$ nc m3-104 20000


> ifconfig
ifconfig
Iface  6  HWaddr: 6F:BD  Channel: 11  Page: 0  NID: 0x18ca  PHY: O-QPSK 
          
          Long HWaddr: 6E:79:49:9F:B1:BF:EF:BD 
           TX-Power: 0dBm  State: IDLE  max. Retrans.: 3  CSMA Retries: 4 
          AUTOACK  ACK_REQ  CSMA  L2-PDU:102  MTU:1280  HL:64  RTR  
          6LO  IPHC  
          Source address length: 8
          Link type: wireless
          inet6 addr: fe80::6c79:499f:b1bf:efbd  scope: link  VAL
          inet6 group: ff02::2
          inet6 group: ff02::1
          inet6 group: ff02::1:ffbf:efbd
          inet6 group: ff02::1a
          
          Statistics for Layer 2
            RX packets 25  bytes 1061
            TX packets 10 (Multicast: 10)  bytes 416
            TX succeeded 10 errors 0
          Statistics for IPv6
            RX packets 25  bytes 1586
            TX packets 10 (Multicast: 10)  bytes 626
            TX succeeded 10 errors 0

> ip addr show | grep tap
ip addr show | grep tap
shell: command not found: ip
> 

> ping 2a00:1450:4007:80f::2003
ping 2a00:1450:4007:80f::2003
12 bytes from 2a00:1450:4007:80f::2003: icmp_seq=0 ttl=113 rssi=-43 dBm time=28.614 ms
12 bytes from 2a00:1450:4007:80f::2003: icmp_seq=1 ttl=113 rssi=-43 dBm time=36.860 ms
12 bytes from 2a00:1450:4007:80f::2003: icmp_seq=2 ttl=113 rssi=-43 dBm time=29.495 ms

--- 2a00:1450:4007:80f::2003 PING statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 28.614/31.656/36.860 ms


munozbar@grenoble:~$ ip -6 route | grep tap1
2001:660:5307:3100::/64 via fe80::2 dev tap1 metric 1024 pref medium
fe80::/64 dev tap1 proto kernel metric 256 pref medium
munozbar@grenoble:~$ 

---


### 1.3

![[Pasted image 20260621133927.png]]


![[Pasted image 20260621133959.png]]

Todos excepto 105 recibieron perfil de sniffer

en 103
![[Pasted image 20260621134106.png]]

Esperando paquete

![[Pasted image 20260621134754.png]]

![[Pasted image 20260621134804.png]]

![[Pasted image 20260621134945.png]]

![[Pasted image 20260621134953.png]]


## Actividad 2

### 2.1


![[Pasted image 20260621191510.png]]
![[Pasted image 20260621192158.png]]
