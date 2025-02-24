##### Configure Networking Using DHCP
- If you want the server to automatically obtain an IP address from a DHCP server, you’ll need to enable DHCP on your network interface.
- Open the network configuration file for the interface (e.g., eth0):
- sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
BOOTPROTO=dhcp
ONBOOT=yes
sudo systemctl restart network


##### netplan:
