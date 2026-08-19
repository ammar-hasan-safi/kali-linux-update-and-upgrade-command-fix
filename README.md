**Setup**

## Debian/Ubuntu
**Apply all of this command to fix this issue**

### 1. এটি যা করবে:

/etc/apt/sources.list সরিয়ে দেবে (যাতে duplicate না থাকে)।
ডিফল্ট kali.sources ফাইল তৈরি করবে।
APT cache পরিষ্কার করবে।
নতুন করে repository index download করবে।
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

### 2. এরপর যদি সব ঠিক থাকে, সিস্টেম আপগ্রেড করতে চালান:

**Ubuntu 18.04 and above or Debian 10 and above**
```bash
sudo apt full-upgrade -y
```
**এটি Kali Linux-এর ডিফল্ট repository কনফিগারেশনে ফিরিয়ে এনে সর্বশেষ package list ও package আপডেট করবে।**

### 3. HTTPS mirror ব্যবহার করুন:
```bash
sudo sed -i 's|http://http.kali.org/kali|https://kali.download/kali|g' /etc/apt/sources.list.d/kali.sources
sudo apt clean
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
```

### 4. এরপর যদি সব ঠিক থাকে, সিস্টেম আপডেট && আপগ্রেড করতে চালান:
```bash
sudo apt update -y && sudo apt upgrade -y && sudo apt full-ugrade
```
