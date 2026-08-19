**Setup**

## Debian/Ubuntu
**Apply this all he command to fix this issue**

### এটি যা করবে:

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

### এরপর যদি সব ঠিক থাকে, সিস্টেম আপডেট করতে চালান:

**Ubuntu 18.04 and above or Debian 10 and above**
```bash
sudo apt full-upgrade -y
```
**এটি Kali Linux-এর ডিফল্ট repository কনফিগারেশনে ফিরিয়ে এনে সর্বশেষ package list ও package আপডেট করবে।

### Other versions
```bash
sudo apt install -y build-essential unzip
wget https://github.com && unzip master.zip
cd pixiewps*/
make
sudo make install
```

### Getting OneShot
```bash
cd ~
wget https://raw.githubusercontent.com/drygdryg/OneShot/master/oneshot.py
```
