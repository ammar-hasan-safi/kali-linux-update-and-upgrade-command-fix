বেশিরভাগ সময় Kali mirror sync হওয়ার সময় বা APT cache corrupt হলে এমন হয়। 


নিচের command-গুলো একসাথে চালাতে পারেন:

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

এটি যা করবে:

/etc/apt/sources.list সরিয়ে দেবে (যাতে duplicate না থাকে)।
ডিফল্ট kali.sources ফাইল তৈরি করবে।
APT cache পরিষ্কার করবে।
নতুন করে repository index download করবে।


HTTPS mirror ব্যবহার করুন:

sudo sed -i 's|http://http.kali.org/kali|https://kali.download/kali|g' /etc/apt/sources.list.d/kali.sources
sudo apt clean
sudo rm -rf /var/lib/apt/lists/*
sudo apt update
সমাধান ২

যদি তবুও না হয়, ৩০ মিনিট থেকে কয়েক ঘণ্টা অপেক্ষা করে আবার চালান:

sudo apt update

Mirror sync শেষ হলে সমস্যাটি নিজে থেকেই চলে যায়।
