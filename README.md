# deploy-node-vps

Servidor
# 1 - Actualizamos
```
apt-get update && apt-get upgrade -y
```

# 2- Instalamos  NVM

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
source ~/.bashrc

3- Instalamos Node
nvm install node
node —version

4- Creamos la carpeta proyecto y clonamos
mkdir proyects
cd proyects

5- Clonamos la app
git clone https://github.com/react-spain/node-react-inicio.git
cd node-react-inicio

6- Instalamos los paquetes
npm install

7- instalamos PM2 
npm install pm2 -g
pm2 start app.js
pm2 startup systemd
pm2 list
sudo systemctl status pm2-root
sudo systemctl start pm2-root
Q

8- Instalamos Ngix
sudo apt-get install nginx -y
cd /etc/nginx/sites-available
nano default

========= Editamos Location ===================
location / {
                proxy_pass http://localhost:8081;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
                proxy_set_header Host $host;
                proxy_cache_bypass $http_upgrade;
        }
============================
nginx -t
nginx -s reload

