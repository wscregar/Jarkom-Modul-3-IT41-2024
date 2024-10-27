# Jarkom-Modul-3-IT41-2024
*Anggota kelompok IT41*:
| Nama      | NRP         |
  |-----------|-------------| 
  | Wira Samudra Siregar  | 5027231041  |
  | Adi Satria Pangestu | 5027231043 |

# Topologi

![image](https://github.com/user-attachments/assets/a1f6ba8e-2aa4-46c2-990c-25be4b5f9d10)

# IP

## Node IP:

### Paradis(dhcp relay):

    1. eth0  dhcp

    2. eth1	192.237.1.1	

    3. eth2	192.237.2.1	

    4. eth3	192.237.3.1	

    5. eth4	192.237.4.1

### Tybur(dhcp Server):

    eth0	192.237.4.2	

    gateway 192.237.4.1

### Fritz(dns Server):

      eth0	192.237.4.3	

      gateway 192.237.4.1

### Warhammer(Database Server):

    eth0	192.237.3.4	

    gateway 192.237.3.1

### Beast(Load Balancer Laravel):

    eth0	192.237.3.2	

    gateway 192.237.3.1

### Colossal(Load Balancer PHP):

    eth0	192.237.3.3	

    gateway 192.237.3.1

### Annie(Laravel Worker):

    eth0	192.237.1.2	

    gateway 192.237.1.1

### Bertholdt(Laravel Worker)	

    eth0	192.237.1.3	

    gateway 192.237.1.1

### Reiner(Laravel Worker):

    eth0	192.237.1.4	

    gateway 192.237.1.1

### Armin(PHP Worker):

    eth0	192.237.2.4	

    gateway 192.237.2.1

### Eren(PHP Worker):

    eth0	192.237.2.3	

    gateway 192.237.2.1

### Mikasa(PHP Worker):

    eth0	192.237.2.2	

    gateway 192.237.2.1

### Zeke(Client):

    eth0	DHCP	

### Erwin(Client):	

    eth0	DHCP	

## Konfigurasi IP:

1. Paradis
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.237.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.237.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.237.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.237.4.1
	netmask 255.255.255.0
 
2. Tybur

auto eth0
iface eth0 inet static
	address 192.237.4.2
	netmask 255.255.255.0
	gateway 192.237.4.1
 
3. Fritz

auto eth0
iface eth0 inet static
	address 192.237.4.3
	netmask 255.255.255.0
	gateway 192.237.4.1

4. Warhammer

auto eth0
iface eth0 inet static
	address 192.237.3.4
	netmask 255.237.255.0
	gateway 192.237.3.1

5. Beast

auto eth0
iface eth0 inet static
	address 192.237.3.2
	netmask 255.237.255.0
	gateway 192.237.3.1

6. Colossal

auto eth0
iface eth0 inet static
	address 192.237.3.3
	netmask 255.237.255.0
	gateway 192.237.3.1

7. Annie

auto eth0
iface eth0 inet static
	address 19.237.1.2
	netmask 255.255.255.0
	gateway 192.237.1.1

8. Bertholdt

auto eth0
iface eth0 inet static
	address 19.237.1.3
	netmask 255.255.255.0
	gateway 192.237.1.1

9. Reiner

auto eth0
iface eth0 inet static
	address 19.237.1.4
	netmask 255.255.255.0
	gateway 192.237.1.1

10. Armin

auto eth0
iface eth0 inet static
	address 192.237.2.4
	netmask 255.255.255.0
	gateway 192.237.2.1

11. Eren

auto eth0
iface eth0 inet static
	address 192.237.2.3
	netmask 255.255.255.0
	gateway 192.237.2.1

12. Mikasa

auto eth0
iface eth0 inet static
	address 192.237.2.2
	netmask 255.255.255.0
	gateway 192.237.2.1
 
13. Zeke

auto eth0
iface eth0 inet dhcp

14. Erwin

auto eth0
iface eth0 inet dhcp


## Setup Node

DHCP Relay (Paradis)

    iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.246.0.0/16
    apt-get update
    apt install isc-dhcp-relay -y
