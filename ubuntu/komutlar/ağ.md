https://www.youtube.com/watch?v=536RYpG3OJw&list=PLeKWVPCoT9e2n-VV5_7waHCxqMQsf4aBO&index=14&ab_channel=S%C3%BCleyman%C5%9EEKER

# ifconfig 

ip almaya yarar

```bash
ifconfig -a

enp1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
       

```

**ether** => ethernet kartının numarası
**inet** => ip adresi

# ayarların olduğu dosya

```bash
cat /etc/hots

127.0.0.1	localhost
127.0.1.1	ahmet

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```



yukarıdaki ayarları düzenlersek kalıcı olarak ip adreslerini değiştirmiş oluruz



# ip kapatma

> ipconfig wlp2s0 up	# ayağa kaldırı
>
> ipconfig wlp2s0 down	# kapatır



# istek atma

> ping 127.0.0.1



# routing => yönlendirme ipleri

> netstat -rn

```bash
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
```



> route 

ip adreslerini almak için kullanılabilir.

```bash
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    600    0        0 wlp2s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
```



# ip alma yöntem 

> ip addr

# static ip tanımlama

https://www.youtube.com/watch?v=-eFKSRGMbEM&list=PLeKWVPCoT9e1tqsgPTQabtumX6E1XpAhz&index=11&ab_channel=S%C3%BCleyman%C5%9EEKER

