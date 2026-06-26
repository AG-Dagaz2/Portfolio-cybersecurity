## Network Design

The homelab is connected behind the ISP router and accessed through a mesh Wi-Fi network based on TP-Link.

Three wireless networks are configured:

- Private Network
- IoT Network
- Guest Network

Administrative access to internal services is performed through WireGuard VPN with DDNS.

Every services is only accessible on the VPN and internal interface. Only the VPN service required a portforwarding on the ISP router.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b6fdfbb0-1132-423e-b8eb-fc12ebeac42e" />
