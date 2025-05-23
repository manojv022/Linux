
Netplan is a utility for easily configuring networking on Linux systems, particularly those using **systemd-networkd** or **NetworkManager** as a backend. It is most commonly used on **Ubuntu 17.10 and later**.

---

### 🔧 What is Netplan?

Netplan allows you to configure networking using **YAML configuration files**, which are then translated into backend-specific configurations. It simplifies network configuration, especially for **cloud instances**, servers, and systems needing complex network setups (e.g., static IPs, bridges, bonds, VLANs).

---

### 📁 Configuration Files

Netplan configuration files are stored in:

```bash
/etc/netplan/
```

Typically named like `01-netcfg.yaml`, `50-cloud-init.yaml`, etc.

---

### 📌 Example: Adding a Static IP Configuration

Suppose you want to assign a static IP to your network interface (e.g., `eth0`):

1. Open or create a YAML file in `/etc/netplan/`:

```bash
sudo nano /etc/netplan/01-netcfg.yaml
```

2. Add this configuration:

```yaml
network:
  version: 2
  ethernets:
    eth0:
      dhcp4: no
      addresses: [192.168.1.100/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
```

3. Apply the changes:

```bash
sudo netplan apply
```

To debug:

```bash
sudo netplan try
```

---

### ❓ Why Use Netplan? Importance

* **Unified configuration**: Clean YAML syntax instead of multiple files across `/etc/network/` and `/etc/systemd/`.
* **Supports cloud-init**: Common on cloud servers for automated setup.
* **Backed by modern services**: Works with NetworkManager (for desktops) and systemd-networkd (for servers).
* **Easier management**: Especially useful for automated or scripted deployments.

---

### 🛠 Common Use Cases

* Setting static IPs
* Defining VLANs, bridges, or bonded interfaces
* Managing Wi-Fi settings (with NetworkManager)
* Configuring routes, MTUs, and nameservers

