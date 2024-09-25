## Server Configuration

##### OS : Ubuntu 20.04

`sudo apt update`

###### - Install GIT

`sudo apt install git`

###### - Install Node JS and NPM

`sudo apt install nodejs npm`
`node -v`
`npm -v`

- Update to latest
  `curl -fsSL https://deb.nodesource.com/setup_21.x | sudo -E bash - &&\ sudo apt-get install -y nodejs`
  `npm install -g npm`
  `node -v`
  `npm -v`

- Install PM2 for managing node js app
  `npm install pm2@latest -g`
  `pm2 -v`
  `pm2 ls`

###### - Install Nginx on Host Machine

src : https://www.linuxbabe.com/ubuntu/install-nginx-latest-version-ubuntu-18-04
src : https://www.nginx.com/resources/wiki/start/topics/tutorials/install/

###### - Install UFW for ruling firewall access

`sudo apt-get update`
`sudo apt-get install ufw`

- Enable UFW `sudo ufw enable`
- Disable UFW `sudo ufw disable` For disabling all firewall rule
- Check Status and open port `sudo ufw status`
- Only allow for port 80, 443 (ssl) and 22 (SSH)
  `sudo ufw allow 80`
  `sudo ufw allow 443`
  `sudo ufw allow 22`
- Deny specific port `sudo ufw deny 3000`, normally we don;t need to set this, it will automatically block all port if we enable UFW
- Allow IP Adress To Access SSH `sudo ufw allow from 110.138.84.0`
- Remove IP Address`sudo ufw delete allow from 110.138.84.0`

###### - Install Certbot for Let's Encrypt

`sudo apt install certbot`

###### - Install Docker Engine

URL : https://docs.docker.com/engine/install/ubuntu/

1. Set up Docker's `apt` repository

<pre>
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
</pre>

2. Install the Docker packages.

<pre>
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
</pre>

3. Verify that the Docker Engine installation is successful by running the `hello-world` image.

<pre>
sudo service docker start
sudo docker run hello-world
</pre>

---

## Docker Configuration

#### - Installation

- run `docker-compose up -d`

<details>
  <summary>Geoserver Setting</summary>

- Geoserver open in `http://localhost:5050/geoserver` with username: `admin` and password: `geoserver`
- Change Geoserver admin password

</details>
