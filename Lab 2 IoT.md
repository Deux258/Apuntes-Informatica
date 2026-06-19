
id = 440803

CHANNEL=26
PAN_ID=0xfe0d


![[Pasted image 20260618163114.png]]

[
    "m3-10.grenoble.iot-lab.info",
    "m3-11.grenoble.iot-lab.info",
    "m3-12.grenoble.iot-lab.info",
    "m3-13.grenoble.iot-lab.info"
]

![[Pasted image 20260618163237.png]]

env: CHANNEL=21
env: PAN_ID=0xb535

![[Pasted image 20260618163637.png]]

text	   data	    bss	    dec	    hex	filename
  90552	    188	  18980	 109720	  1ac98	/home/jovyan/work/training/riot/RIOT/examples/gnrc_networking/bin/iotlab-m3/gnrc_networking.elf
make: Leaving directory '/home/jovyan/work/training/riot/RIOT/examples/gnrc_networking'

![[Pasted image 20260618164456.png]]

![[Pasted image 20260618164507.png]]


fe80::7890:3c7d:ec49:584d  scope: link  VAL


![[Pasted image 20260618164518.png]]

fe80::a4a3:d9fd:4933:779  scope: link  VAL


![[Pasted image 20260618164757.png]]



![[Pasted image 20260618165342.png]]

![[Pasted image 20260618165359.png]]


text	   data	    bss	    dec	    hex	filename
  80048	    144	  22188	 102380	  18fec	/home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router/bin/iotlab-m3/gnrc_border_router.elf
iotlab-node --jmespath='keys(@)[0]' --format='lambda ret: exit(int(ret))'  --list grenoble,m3,12 --flash /home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router/bin/iotlab-m3/gnrc_border_router.bin
make: Leaving directory '/home/jovyan/work/training/riot/RIOT/examples/gnrc_border_router'


![[Pasted image 20260618170603.png]]

![[Pasted image 20260618170611.png]]





