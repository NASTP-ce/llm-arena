# 🛠 Steps to Setup NFS Server & Clients

## 1. Pick one system as the **NFS server**

Let’s say the server’s IP is `192.168.1.10`.

Install NFS server:

```bash
sudo apt update
sudo apt install nfs-kernel-server -y
```

---

## 2. Create the shared folder

```bash
sudo mkdir -p /srv/shared
sudo chown nobody:nogroup /srv/shared
sudo chmod 777 /srv/shared
```

*(You can later lock down permissions for specific users/groups.)*

---

## 3. Configure exports

Open `/etc/exports` and add a rule:

```bash
sudo nano /etc/exports
```

Add:

```
/srv/shared 192.168.1.0/24(rw,sync,no_subtree_check)
```

* `192.168.1.0/24` → allows all clients in your LAN
* `rw` → read/write access
* `sync` → writes committed immediately
* `no_subtree_check` → avoids permission headaches

Apply changes:

```bash
sudo exportfs -ra
sudo systemctl restart nfs-kernel-server
```

---

## 4. Open firewall (if enabled)

```bash
sudo ufw allow from 192.168.1.0/24 to any port nfs
```

---

## 5. Configure clients (all other 4 systems)

Install NFS tools:

```bash
sudo apt install nfs-common -y
```

Create mount point:

```bash
sudo mkdir -p /mnt/shared
```

Mount NFS share:

```bash
sudo mount 192.168.1.10:/srv/shared /mnt/shared
```

Check:

```bash
df -h | grep shared
```

---

## 6. Make it permanent (on clients)

Add this line to `/etc/fstab`:

```
192.168.1.10:/srv/shared   /mnt/shared   nfs   defaults   0   0
```

Now the folder will auto-mount on boot.

---

✅ Now all 5 systems can read/write to `/mnt/shared` and see the same files.

---
