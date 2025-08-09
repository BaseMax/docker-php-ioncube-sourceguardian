# Docker PHP with ionCube & SourceGuardian Loaders

A ready-to-use Docker environment for running PHP with **ionCube** and **SourceGuardian** loaders pre-installed, plus a wide range of helpful PHP extensions and CLI tools.

> Built and maintained by [BaseMax](https://github.com/BaseMax) © 2025, MIT Licensed

---

## 🧩 Features

* PHP Composer
* PHP 7.4, 8.1, 8.2, 8.3, 8.4 (custom Dockerfile)
* **ionCube Loader** and **SourceGuardian** auto-installed
* Common PHP extensions: `mysqli`, `pdo_mysql`, `intl`, `mbstring`, `gd`, `bcmath`, `soap`, etc.
* Popular PECL extensions: `redis`
* Useful CLI tools: `sudo`, `htop`, `nano`, `curl`, `git`, `ping`, and more
* Fully dockerized using `docker-compose`
* Includes MariaDB 11 with persistent volumes

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/BaseMax/docker-php-ioncube-sourceguardian.git
cd docker-php-ioncube-sourceguardian
```

### 2. Setup environment

Copy `.env.example` to `.env` and fill in your desired credentials:

```bash
cp .env.example .env
```

Edit the `.env` file and set your variables:

```env
SERVICE_USER_PHP=php
SERVICE_PASSWORD_PHP=your_password
SERVICE_PASSWORD_ROOT=your_root_password
```

### 3. Build and start the services

```bash
docker compose up
```

Or run in the background:

```bash
docker compose up -d
```

---

## 📁 Project Structure

```
.
├── Dockerfile            # Custom Dockerfile based on php:php8.1
├── docker-compose.yml    # Docker Compose setup for PHP and MariaDB
├── .env.example          # Sample environment file
├── LICENSE               # MIT License
└── README.md             # You are here
```

---

## 🧱 Dockerfile Overview

Your WordPress container is enhanced with:

* Development & debug tools (`nano`, `htop`, `screenfetch`, `git`, etc.)
* PHP extensions via `docker-php-ext-install` and PECL
* Auto-installation of `ionCube` and `SourceGuardian` from:
  [BaseMax/php-installer-ioncube-sourceguardian](https://github.com/BaseMax/php-installer-ioncube-sourceguardian)

---

## 🐬 MariaDB Configuration

MariaDB runs with the following environment variables from `.env`:

```env
MYSQL_ROOT_PASSWORD
MYSQL_DATABASE
MYSQL_USER
MYSQL_PASSWORD
```

Data is persisted to `xg4c44cgg8ok0cc4c0k8c448_mariadb-data` volume.

---

## 🧪 Health Checks

Both services include built-in healthchecks for stability:

* **WordPress**: via `curl http://127.0.0.1`
* **MariaDB**: via `healthcheck.sh --connect --innodb_initialized`

---

## Build Docker

```bash
docker login
docker build --build-arg PHP_IMAGE=7.4 -t basemax/php-ioncube-sourceguardian:7.4 .
docker build --build-arg PHP_IMAGE=8.1 -t basemax/php-ioncube-sourceguardian:8.1 .
docker build --build-arg PHP_IMAGE=8.2 -t basemax/php-ioncube-sourceguardian:8.2 .
docker build --build-arg PHP_IMAGE=8.3 -t basemax/php-ioncube-sourceguardian:8.3 .
docker build --build-arg PHP_IMAGE=8.4 -t basemax/php-ioncube-sourceguardian:8.4 .
docker push basemax/php-ioncube-sourceguardian:7.4
docker push basemax/php-ioncube-sourceguardian:8.1
docker push basemax/php-ioncube-sourceguardian:8.2
docker push basemax/php-ioncube-sourceguardian:8.3
docker push basemax/php-ioncube-sourceguardian:8.4
```

---

## 📝 License

This project is licensed under the MIT License.

© 2025 [Max Base](https://github.com/BaseMax)
