**Setup**

## Debian/Ubuntu/Kali Linux
**Apply all of this command to fix this issue**

### 1. This will: 

Remove `/etc/apt/sources.list` (to avoid duplicates). Create a default `kali.sources` file. Clear the APT cache. Download the repository index anew.
```bash
sudo rm -f /etc/apt/sources.list && \
sudo tee /etc/apt/sources.list.d/kali.sources >/dev/null <<EOF
Types: deb
URIs: http://http.kali.org/kali/
Suites: kali-rolling
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/kali-archive-keyring.gpg
EOF
sudo apt clean && \
sudo rm -rf /var/lib/apt/lists/* && \
sudo apt update
```

### 2. If everything is in order, run the following command to upgrade the system:

**Ubuntu 18.04 and above or Debian 10 and above And Kali Linux**
```bash
sudo apt full-upgrade -y
```
**এটি Kali Linux-এর ডিফল্ট repository কনফিগারেশনে ফিরিয়ে এনে সর্বশেষ package list ও package আপডেট করবে।**

### 3. Use an HTTPS mirror:

```bash
sudo sed -i 's|http://http.kali.org/kali|https://kali.download/kali|g' /etc/apt/sources.list.d/kali.sources
sudo apt clean
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

### 4. If everything is in order, run the following command to update and upgrade the system:

```bash
sudo apt update -y && sudo apt upgrade -y && sudo apt full-ugrade
```
