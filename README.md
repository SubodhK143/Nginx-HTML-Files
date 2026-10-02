# 🌐 Nginx Multi-Website Hosting — 7 Websites on 7 Ports

![Nginx](https://img.shields.io/badge/Nginx-Web%20Server-green?style=for-the-badge\&logo=nginx)
![Linux](https://img.shields.io/badge/Linux-Server-black?style=for-the-badge\&logo=linux)
![HTML](https://img.shields.io/badge/HTML-Websites-orange?style=for-the-badge\&logo=html5)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

## 📌 Project Overview

This project demonstrates how to configure **Nginx to host multiple independent websites on a single Linux server**, with each website listening on a different TCP port.

In this setup, **7 different HTML websites** are created under separate directories and served through Nginx on ports **8081–8087**.

This is a practical example of **multi-site hosting, Nginx server configuration, Linux web-server administration, and port-based traffic routing**.

---

## 🏗️ Architecture

```text
                         Linux Server
                              │
                            Nginx
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
       Port 8081           Port 8082           Port 8083
          │                   │                   │
       Site 1              Site 2              Site 3
          │                   │                   │
   /var/www/site1      /var/www/site2      /var/www/site3

          ┌───────────────────┼───────────────────┐
          │                   │                   │
       Port 8084           Port 8085           Port 8086
          │                   │                   │
       Site 4              Site 5              Site 6
          │                   │                   │
   /var/www/site4      /var/www/site5      /var/www/site6

                              │
                           Port 8087
                              │
                           Site 7
                              │
                       /var/www/site7
```

---

## 🎯 Project Objectives

* Configure Nginx as a web server
* Host multiple websites on a single server
* Configure different listening ports
* Create separate website document roots
* Understand Nginx `server` blocks
* Practice Linux file and directory management
* Verify websites using `curl`
* Understand port-based request routing

---

## 🗂️ Website Configuration

| Website      | Document Root    |   Port | Theme                  |
| ------------ | ---------------- | -----: | ---------------------- |
| 🌐 Website 1 | `/var/www/site1` | `8081` | Black / Lime           |
| 🌐 Website 2 | `/var/www/site2` | `8082` | Navy / Cyan            |
| 🌐 Website 3 | `/var/www/site3` | `8083` | Purple / Cyan Gradient |
| 🌐 Website 4 | `/var/www/site4` | `8084` | Black / Yellow         |
| 🌐 Website 5 | `/var/www/site5` | `8085` | Red / Orange Gradient  |
| 🌐 Website 6 | `/var/www/site6` | `8086` | Dark Green             |
| 🌐 Website 7 | `/var/www/site7` | `8087` | Navy / Blue Gradient   |

---

# 🛠️ Implementation

## 1. Install Nginx

For Amazon Linux:

```bash
sudo dnf install nginx -y
```

For Ubuntu:

```bash
sudo apt update
sudo apt install nginx -y
```

Start and enable Nginx:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Check the service:

```bash
sudo systemctl status nginx
```

---

## 2. Create Website Directories

```bash
sudo mkdir -p /var/www/site1
sudo mkdir -p /var/www/site2
sudo mkdir -p /var/www/site3
sudo mkdir -p /var/www/site4
sudo mkdir -p /var/www/site5
sudo mkdir -p /var/www/site6
sudo mkdir -p /var/www/site7
```

---

# 📄 3. Create Website HTML Files

## Website 1 — Port 8081

```bash
sudo tee /var/www/site1/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 1</title>
    <style>
        body {
            background-color: black;
            color: lime;
            text-align: center;
            padding-top: 200px;
            font-family: Arial;
        }
    </style>
</head>
<body>
    <h1>Website 1</h1>
    <h3>Running on Port 8081</h3>
</body>
</html>
EOF
```

---

## Website 2 — Port 8082

```bash
sudo tee /var/www/site2/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
<style>
body {
    background-color: navy;
    color: cyan;
    text-align: center;
    padding-top: 200px;
}
</style>
</head>
<body>
<h1>Website 2</h1>
<h3>Running on Port 8082</h3>
</body>
</html>
EOF
```

---

## Website 3 — Port 8083

```bash
sudo tee /var/www/site3/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 3</title>
    <style>
        body {
            background: linear-gradient(to right, purple, cyan);
            color: white;
            text-align: center;
            padding-top: 200px;
            font-family: Arial;
        }
    </style>
</head>
<body>
    <h1>Website 3</h1>
    <h3>Running on Port 8083</h3>
</body>
</html>
EOF
```

---

## Website 4 — Port 8084

```bash
sudo tee /var/www/site4/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 4</title>
    <style>
        body {
            background-color: black;
            color: yellow;
            text-align: center;
            padding-top: 200px;
            font-family: Verdana;
        }
    </style>
</head>
<body>
    <h1>Website 4</h1>
    <h3>Running on Port 8084</h3>
</body>
</html>
EOF
```

---

## Website 5 — Port 8085

```bash
sudo tee /var/www/site5/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 5</title>
    <style>
        body {
            background: linear-gradient(to right, red, orange);
            color: white;
            text-align: center;
            padding-top: 200px;
            font-family: sans-serif;
        }
    </style>
</head>
<body>
    <h1>Website 5</h1>
    <h3>Running on Port 8085</h3>
</body>
</html>
EOF
```

---

## Website 6 — Port 8086

```bash
sudo tee /var/www/site6/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 6</title>
    <style>
        body {
            background-color: darkgreen;
            color: white;
            text-align: center;
            padding-top: 200px;
            font-family: Georgia;
        }
    </style>
</head>
<body>
    <h1>Website 6</h1>
    <h3>Running on Port 8086</h3>
</body>
</html>
EOF
```

---

## Website 7 — Port 8087

```bash
sudo tee /var/www/site7/index.html > /dev/null <<EOF
<!DOCTYPE html>
<html>
<head>
    <title>Website 7</title>
    <style>
        body {
            background: linear-gradient(to right, navy, blue);
            color: cyan;
            text-align: center;
            padding-top: 200px;
            font-family: Courier New;
        }
    </style>
</head>
<body>
    <h1>Website 7</h1>
    <h3>Running on Port 8087</h3>
</body>
</html>
EOF
```

---

# ⚙️ 4. Configure Nginx

Create a configuration file:

```bash
sudo vi /etc/nginx/conf.d/multi-site.conf
```

Add:

```nginx
server {
    listen 8081;
    server_name _;
    root /var/www/site1;

    index index.html;
}

server {
    listen 8082;
    server_name _;
    root /var/www/site2;

    index index.html;
}

server {
    listen 8083;
    server_name _;
    root /var/www/site3;

    index index.html;
}

server {
    listen 8084;
    server_name _;
    root /var/www/site4;

    index index.html;
}

server {
    listen 8085;
    server_name _;
    root /var/www/site5;

    index index.html;
}

server {
    listen 8086;
    server_name _;
    root /var/www/site6;

    index index.html;
}

server {
    listen 8087;
    server_name _;
    root /var/www/site7;

    index index.html;
}
```

---

# 🔍 5. Test Nginx Configuration

Always validate the configuration before restarting:

```bash
sudo nginx -t
```

Expected:

```text
syntax is ok
test is successful
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

---

# 🔥 6. Allow Ports in Firewall

If using AWS EC2, add inbound rules to the **Security Group**:

```text
TCP 8081
TCP 8082
TCP 8083
TCP 8084
TCP 8085
TCP 8086
TCP 8087
```

For a Linux firewall using firewalld:

```bash
sudo firewall-cmd --permanent --add-port=8081-8087/tcp
sudo firewall-cmd --reload
```

Verify:

```bash
sudo firewall-cmd --list-ports
```

---

# 🧪 7. Verify Websites

Check listening ports:

```bash
sudo ss -tulpn | grep nginx
```

Test locally:

```bash
curl http://localhost:8081
curl http://localhost:8082
curl http://localhost:8083
curl http://localhost:8084
curl http://localhost:8085
curl http://localhost:8086
curl http://localhost:8087
```

Or access from your browser:

```text
http://SERVER-IP:8081
http://SERVER-IP:8082
http://SERVER-IP:8083
http://SERVER-IP:8084
http://SERVER-IP:8085
http://SERVER-IP:8086
http://SERVER-IP:8087
```

---

# 📊 Expected Result

```text
SERVER-IP
    │
    └── Nginx
         │
         ├── :8081 → /var/www/site1 → Website 1
         ├── :8082 → /var/www/site2 → Website 2
         ├── :8083 → /var/www/site3 → Website 3
         ├── :8084 → /var/www/site4 → Website 4
         ├── :8085 → /var/www/site5 → Website 5
         ├── :8086 → /var/www/site6 → Website 6
         └── :8087 → /var/www/site7 → Website 7
```

---

# 🧠 Key Concepts Learned

### Nginx

* Web server configuration
* Server blocks
* Listening ports
* Document roots
* Static content serving

### Linux

* Directory management
* File permissions
* Services
* `systemctl`
* `ss`
* `curl`
* Firewall configuration

### Networking

* TCP ports
* Port-based traffic routing
* Inbound firewall rules
* Client-server communication

### Troubleshooting

Useful commands:

```bash
sudo nginx -t
sudo systemctl status nginx
sudo systemctl restart nginx
sudo ss -tulpn
sudo journalctl -u nginx
curl -I http://localhost:8081
```

---

# 💼 Real-World Use Case

This setup represents a simplified version of a scenario where an organization needs to host multiple independent web applications on a shared Linux server.

For example:

```text
Production Server
       │
      Nginx
       │
 ┌─────┼─────┬─────────────┐
 │     │     │             │
App-1 App-2 App-3       App-7
8081  8082  8083        8087
```

In a larger production environment, this concept can be extended using:

* DNS
* Domain-based routing
* HTTPS / SSL certificates
* Reverse proxy
* Load balancing
* Docker containers
* AWS Application Load Balancer
* Auto Scaling
* CI/CD pipelines
* Monitoring with Prometheus & Grafana

---

# 🚀 Possible Improvements

Future enhancements for this project:

* [ ] Configure domain-based virtual hosting
* [ ] Add HTTPS using SSL/TLS
* [ ] Configure Nginx reverse proxy
* [ ] Add AWS Application Load Balancer
* [ ] Containerize websites using Docker
* [ ] Implement CI/CD with Jenkins
* [ ] Add Prometheus monitoring
* [ ] Add Grafana dashboards
* [ ] Configure centralized Nginx access/error logging
* [ ] Deploy infrastructure using Terraform

---

# 📁 Suggested Repository Structure

```text
nginx-multi-site-hosting/
│
├── README.md
│
├── site1/
│   └── index.html
│
├── site2/
│   └── index.html
│
├── site3/
│   └── index.html
│
├── site4/
│   └── index.html
│
├── site5/
│   └── index.html
│
├── site6/
│   └── index.html
│
└── site7/
    └── index.html
```

---

# 🎯 Interview Explanation

> **"I configured Nginx on a Linux server to host seven independent static websites. Each website had its own document root under `/var/www` and was exposed through a separate TCP port from 8081 to 8087. I configured individual Nginx server blocks, validated the configuration using `nginx -t`, restarted the service, opened the required firewall/security-group ports, and verified each application using curl and a browser."**

This project demonstrates practical knowledge of **Linux administration, Nginx, networking, firewall configuration, and web-server troubleshooting**.

---

## 👨‍💻 Author

**Subodh Kumar**

AWS Cloud / DevOps Engineer

🔗 **LinkedIn:** [Subodh Kumar](https://www.linkedin.com/in/subodh-kumar-aws-certified/)

---

## ⭐ If You Found This Useful

If this project helped you understand Nginx multi-site hosting, consider giving the repository a ⭐ on GitHub.
