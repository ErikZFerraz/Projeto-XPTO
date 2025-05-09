<!---

https://50.17.29.135/
https://54.82.29.243/
http://13.218.220.17/


    server 50.17.29.135;
    server 54.82.29.243;
    server 13.218.220.17;

Editar configuração NGINX:
bash
Copiar
Editar
sudo nano /etc/nginx/sites-available/default
Substitua tudo por:

nginx
Copiar
Editar
upstream backends {
    server <IP_PRIVADO_SERVER1>;
    server <IP_PRIVADO_SERVER2>;
    server <IP_PRIVADO_SERVER3>;
}

server {
    listen 80;

    location / {
        proxy_pass http://backends;
    }
}

sudo systemctl restart nginx

98.81.78.48

pscp -i C:\caminho\para\minhachave.ppk ubuntu@98.81.78.48:/etc/openvpn/server/chave.key C:\Users\SeuUsuario\Desktop\


Se você quer reinstalar o Nginx no seu sistema usando o apt, siga estes passos:

🧹 1. Remover o Nginx completamente:
Isso remove o Nginx e todos os arquivos de configuração:

bash
Copiar
Editar
sudo apt purge -y nginx nginx-common
sudo apt autoremove -y
🧽 2. (Opcional) Remover arquivos restantes:
Se quiser garantir que tudo seja limpo:

bash
Copiar
Editar
sudo rm -rf /etc/nginx /var/www/html /var/log/nginx

🔄 3. Atualizar os pacotes:
bash
Copiar
Editar
sudo apt update
📦 4. Reinstalar o Nginx:
bash
Copiar
Editar
sudo apt install -y nginx
Depois disso, verifique se está rodando:

bash
Copiar
Editar
systemctl status nginx

🌐 3. Instalar e Configurar NGINX nos Servers (SERVER1, 2 e 3)
Em cada instância:
bash
Copiar
Editar
# Atualize os pacotes
sudo apt update

# Instale o NGINX
sudo apt install -y nginx

# Crie uma página identificadora
echo "Você está conectado ao SERVER1" | sudo tee /var/www/html/index.html

# Reinicie o NGINX
sudo systemctl restart nginx


ls -lah /var/www/html/

-rw-rw-r-- 1 ubuntu ubuntu 3.8K Apr 27 06:44 index.html
-rw-r--r-- 1 root   root    615 Apr 15 00:27 index.nginx-debian.html
-rw-rw-r-- 1 ubuntu ubuntu 9.4K Apr 27 06:44 pong_full.js
drwxrwxr-x 2 ubuntu ubuntu 4.0K Apr 27 06:44 sounds
ubuntu@ip-172-31-24-67:~$



ubuntu@ip-172-31-24-67:~$ ls -lah /var/www/html/
total 32K
drwxr-xr-x 3 root   root   4.0K Apr 27 06:52 .
drwxr-xr-x 3 root   root   4.0K Apr 15 00:27 ..
-rw-rw-r-- 1 ubuntu ubuntu 3.8K Apr 27 06:44 index.html
-rw-r--r-- 1 root   root    615 Apr 15 00:27 index.nginx-debian.html
-rw-rw-r-- 1 ubuntu ubuntu 9.4K Apr 27 06:44 pong_full.js
drwxrwxr-x 2 ubuntu ubuntu 4.0K Apr 27 06:44 sounds
ubuntu@ip-172-31-24-67:~$ -rw-rw-r-- 1 ubuntu ubuntu 3.8K Apr 27 06:44 index.html
-rw-r--r-- 1 root   root    615 Apr 15 00:27 index.nginx-debian.html
-rw-rw-r-- 1 ubuntu ubuntu 9.4K Apr 27 06:44 pong_full.js
drwxrwxr-x 2 ubuntu ubuntu 4.0K Apr 27 06:44 sounds
ubuntu@ip-172-31-24-67:~$


sudo mv /home/ubuntu/index.html /var/www/html/
sudo mv /home/ubuntu/pong_full.js /var/www/html/
sudo mv /home/ubuntu/sounds /var/www/html/ -r

ls -lah /home/ubuntu/
sudo mv /home/ubuntu/sounds /var/www/html/


--->


# Projeto_XPTO
Repositório destinado ao projeto XPTO referente a matéria de Redes de Computadores

---

## 🗺️ Arquitetura do Projeto

![Topologia do Projeto](https://github.com/ErikZFerraz/Projeto-XPTO/blob/main/media/Topografia%20AWS.png)

---

## 🧩 Tecnologias e Serviços Utilizados

- AWS EC2 (Instâncias Ubuntu)
- AWS Security Groups
- NGINX (como proxy reverso / load balancer)
- Docker
- MongoDB
- VPN (OpenVPN ou similar)
- HTML/CSS simples (para teste de backend)
- SSH para provisionamento manual

---

## 🎯 Objetivos do Projeto

- [x] Criar e configurar instâncias EC2 com Ubuntu
- [x] Configurar NGINX nas instâncias backend
- [x] Criar um Load Balancer com NGINX apontando para os backends
- [ ] Configurar VPN para acesso seguro ao ambiente (Sprint 2)
- [ ] Containerizar banco de dados com Docker + MongoDB (Sprint 3)

---

## 📌 Status Atual

✅ **Sprint 1 finalizada**: Load Balancer ativo com 3 servidores backend funcionando e HTML customizado.  
🔄 **Sprint 2 em andamento**: Implementação da VPN e segurança da rede.

---
