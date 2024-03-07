# commands

# install docker and docker compose

sudo apt-get install ca-certificates curl && sudo install -m 0755 -d /etc/apt/keyrings && sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc && sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo chmod 666 /var/run/docker.sock 

sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

# export go path when terminal starts or when you see go not found
export PATH=$PATH:/usr/local/go/bin

# ***********no raft leader elected**********
ifconfig

sudo apt-get install ethtool

sudo ethtool -K <interface> tx off

# install firewallmd

sudo apt -y install firewalld

sudo systemctl start firewalld

sudo systemctl enable firewalld

sudo firewall-cmd --add-port=2376/tcp --permanent

sudo firewall-cmd --add-port=2377/tcp --permanent 

sudo firewall-cmd --add-port=7946/tcp --permanent 

sudo firewall-cmd --add-port=7946/udp --permanent

sudo firewall-cmd --add-port=4789/udp --permanent

sudo firewall-cmd --reload

