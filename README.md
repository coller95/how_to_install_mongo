# how_to_install_mongo


////////
// Mongod 4.4
////////
```console
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
sudo apt-get update
sudo apt-get install -y mongodb-org
```

```console
echo "mongodb-org hold" | sudo dpkg --set-selections
echo "mongodb-org-server hold" | sudo dpkg --set-selections
echo "mongodb-org-shell hold" | sudo dpkg --set-selections
echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
echo "mongodb-org-tools hold" | sudo dpkg --set-selections
```

```console
sudo systemctl start mongod
sudo systemctl daemon-reload
sudo systemctl status mongod
sudo systemctl enable mongod
```

////////
// slice for Mongod 4.4
////////
```console
sudo nano /lib/systemd/system/mongod.slice
```

```
[Slice]
Slice=mongod.slice
MemoryMax=64M
MemorySwapMax=64M
CPUQuota=100%
```

```console
sudo nano /lib/systemd/system/mongod.service
```
```
Slice=mongod.slice
```
