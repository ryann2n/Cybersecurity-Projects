# 🛡️ Week 5 Lab Summary — Hosts File Spoofing & DNS Lookup

This lab focused on understanding how domain name resolution works through DNS and the `/etc/hosts` file. We practiced looking up IP addresses, editing the hosts file, spoofing domains, and observing the effects using Firefox.

---

## ✅ Step 0: Check IP Addresses for Two Different Websites

- Opened Ubuntu VM in VirtualBox.
- Opened the terminal using:  
  `Applications → Terminal Emulator`
- Ran the following commands:
  ```bash
  dig eu.httpbin.org +nocomments
  dig neverssl.com +nocomments
  ```
- Recorded the IP addresses returned for each domain:
  - `eu.httpbin.org` → `<your IP here>`
  - `neverssl.com` → `<your IP here>`
![image](https://github.com/user-attachments/assets/f44dac06-9c4f-4390-a856-390f5cc22a19)


✅ **Checkpoint 0 Complete**

---

## ✅ Step 1: Install Firefox Browser

- Checked if Firefox was installed:
  ```bash
  firefox -v
  ```
- If not found, installed it using:
  ```bash
  sudo apt-get update
  sudo apt-get -y install firefox
  ```
- Verified the browser appears under:  
  `Applications → Internet → Firefox Web Browser`
![image](https://github.com/user-attachments/assets/ea8223b7-8fba-434b-a578-ba9f50d71756)


✅ **Checkpoint 1 Complete**

---

## ✅ Step 2: Navigate to the `/etc` Hosts File

Practiced basic Linux commands:

```bash
cd ~        # Go to home directory
pwd         # Print current directory
cd ..       # Move up one level
cd etc      # Go into /etc directory
ls          # List contents
```

- Located the `hosts` file in `/etc`.

✅ **Checkpoint 2 Complete**

---

## ✅ Step 3: Examine the Hosts File

- Opened the file in view mode:
  ```bash
  nano hosts
  ```
- Observed default entries like:
  ```
  127.0.0.1   localhost
  ::1         localhost
  ```
- Noted the file was unwritable in this mode.
- Exited using `Ctrl + X`.

✅ **Checkpoint 3 Complete**

---

## ✅ Step 4: View Web Pages in the Browser

- Opened Firefox browser.
- Visited both:
  - http://eu.httpbin.org
  - http://www.neverssl.com
- Observed their original page content.
![image](https://github.com/user-attachments/assets/ee001870-edbb-4a9c-a4d1-ed9ce777b678)
![image](https://github.com/user-attachments/assets/97cb0fde-2a52-4f3c-98d2-86ece441427d)


✅ **Checkpoint 4 Complete**

---

## ✅ Step 5: Clear Firefox Browser History

To avoid cached responses affecting results:

1. Opened `History → Manage History → Delete Pages`
2. Opened `Settings → Privacy & Security`
3. Enabled:
   - "Delete cookies and site data when Firefox is closed"
4. Cleared cookies, site data, and browsing history:
   - Disabled "Remember browsing and download history"
   - Disabled "Remember search and form history"
![image](https://github.com/user-attachments/assets/7a073891-c202-4ea8-8d5e-50895ef7124f)


✅ **Checkpoint 5 Complete**

---

## ✅ Step 6: Edit the Hosts File to Spoof IPs

- Reopened hosts file with write access:
  ```bash
  sudo nano hosts
![image](https://github.com/user-attachments/assets/a3206b14-70ca-47b0-aa57-9352b8950c29)

  ```
- Added spoofing entries:
  ```
  <IP of eu.httpbin.org>     www.neverssl.com
  <IP of neverssl.com>       eu.httpbin.org
  ```
- Saved using `Ctrl + O` → Enter  
  Exited using `Ctrl + X`

✅ **Checkpoint 6 Complete**

---

## ✅ Step 7: Confirm Spoofed DNS with `dig`

- Ran:
  ```bash
  dig eu.httpbin.org +nocomments
  dig www.neverssl.com +nocomments
  ```
- Verified that the IP addresses were now **swapped**.

✅ **Checkpoint 7 Complete**

---

## ✅ Step 8: Check Web Pages Again in Firefox

- Revisited:
  - http://eu.httpbin.org
  - http://www.neverssl.com
- Confirmed that:
  - `httpbin.org` now loads neverssl content
  - `neverssl.com` now loads httpbin content

✅ Spoofing verified visually

---

## ✅ Step 9: Restore the Hosts File

- Opened the hosts file:
  ```bash
  sudo nano hosts
  ```
- Removed the spoofing entries.
- Saved and exited.
- Restored Firefox settings (optional):
  - Re-enabled default history/cookie settings

✅ Lab cleanup complete.

---

## 📸 Screenshots

> Screenshots will be added below or uploaded to this folder manually.

---

## 🧠 Reflection: What I Learned

- How to use `dig` to perform DNS lookups
- The purpose and function of the `/etc/hosts` file
- How local spoofing overrides DNS responses
- How browser cache/history can impact DNS testing
- Practical Linux commands for navigation and file editing
  - `cd`, `pwd`, `ls`, `nano`, `sudo`

---

