markdown# Setup

## Debian/Ubuntu

### Installing requirements
```bash
sudo apt install -y python3 wpasupplicant iw wget
```

### Installing Pixiewps
**Ubuntu 18.04 and above or Debian 10 and above**
```bash
sudo apt install -y pixiewps
```

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
