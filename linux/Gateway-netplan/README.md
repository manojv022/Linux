Netplan is a utility for easily configuring networking on Linux systems, particularly those using **systemd-networkd** or **NetworkManager** as a backend. 

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


-------------------------------------------------------------------------------------------------


### 🌐 What Is a Gateway in Networking?

A **gateway** is a device—usually a router—that connects your local network to other networks, most commonly the **internet**. It acts as an access point your computer uses to send data **outside** its local network.

---

### 🏠 In a Home or Office Network:

* Your **gateway** is typically your **router** (e.g., `192.168.1.1`).
* Devices on your network (PCs, phones) send traffic to this gateway when they want to reach sites like `google.com`.

---

### 📤 How It Works:

1. Your PC has an IP, e.g., `192.168.1.100`.
2. You want to visit `openai.com`, which is not on your local network.
3. Your PC sends the request to the **gateway IP** (e.g., `192.168.1.1`).
4. The **gateway routes** that traffic to the internet, finds `openai.com`, and sends the response back.

---

### 📌 In Netplan (Static IP Case):

When you define a static IP, you **must manually specify** a gateway. Here's what this means in Netplan:

```yaml
gateway4: 192.168.1.1
```

This tells your computer:

> "Send all non-local traffic through 192.168.1.1."

Without a gateway, your machine can talk to other local devices, but **not the internet**.

---

### 🚪 Metaphor:

Think of your **gateway** as the **front door** of your house:

* Inside your home = local network
* Outside world = internet
* You must go through the **door (gateway)** to leave your house

---
