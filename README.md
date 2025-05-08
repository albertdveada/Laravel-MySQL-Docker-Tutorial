<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

**[ [🇮🇩 INDONESIAN LANGUAGE VERSION](https://translate.google.com/translate?hl=&sl=en&tl=id&u=https://github.com/albertdveada/Laravel-MySQL-Docker-Tutorial) ]**

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

# Laravel & MySQL Installation with Docker

This repository provides a simple template to install Laravel and MySQL using Docker. It's suitable for beginners and developers who need a quick, isolated, and consistent development environment.

---

## 🚀 Getting Started

### Install Docker

- **Download Docker Desktop**:  
  👉 [Download Docker](https://www.docker.com/products/docker-desktop)  
- **Usage Guide**:  
  👉 [Docker Documentation](https://docs.docker.com/get-started) 

---

## 🪟 Laravel Sail on Windows (Windows Users)

Before using **Laravel Sail**, make sure **WSL (Windows Subsystem for Linux)** and Docker Desktop are installed and active:
**📌 WSL Activation Guide:**  
👉 [How to Enable WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

**1. ✅ Check WSL Installation**

If WSL is installed successfully, you'll see a message like:
   ```powershell
  Downloading: Ubuntu
  Installing: Ubuntu
  Distribution successfully installed. It can be launched via 'wsl.exe -d Ubuntu'
  ```
**2. 🖥️ Open WSL**

Do not open from PowerShell or CMD.
- Press the ``🪟``(Windows) key
- Type ``Ubuntu`` or ``WSL``, then launch the application

**3. 📁 Access Project Folder**

Windows folders are ``mounted`` in WSL under ``/mnt``.
**Example:**
If your project is in ``D:\ProjectLaravel``, run:
   ```bash
  cd /mnt/d/ProjectLaravel
  ```
**⚙️ Install Laravel with Sail**

Replace ``nama-project`` with your desired project name:
   ```bash
  curl -s https://laravel.build/nama-project | bash
  ```
Enter the project folder:
   ```bash
  cd nama-project
  ```
**5. 🚀 Run Laravel**

Activate Sail with:
   ```bash
  ./vendor/bin/sail up
  ```
To run it in the background (optional):
   ```bash
  ./vendor/bin/sail up -d
  ```

---

## 🍎 Laravel Sail on macOS (macOS Users)

**1. 🧱 Create Laravel Project**

Open Terminal and run the following command (replace ``nama-project`` as desired):
   ```bash
  curl -s "https://laravel.build/nama-project" | bash
  ```
**2. 📁 Enter the Project Folder**
   ```bash
  cd nama-project
  ```
**3. 🚀 Run Laravel Sail**
   ```bash
  ./vendor/bin/sail up
  ```
  To run in the *background* (optional):
  ```bash
  ./vendor/bin/sail up -d
  ```

---

## ⚠️ Common Issues

Before accessing `localhost`, ensure the **(session driver)** is set up using the database.

### 🧠 Why Is This Important?
In the `.env`, configuration file, you'll find the following setting:
```env
SESSION_DRIVER=database
  ```
This means Laravel stores session data in the database. If the session table hasn't been created, the app may throw an error when trying to store session data.

**✅ Solution**

Run the following command to create the required session table:
  ```bash
  ./vendor/bin/sail artisan session:table
  ```
Then, proceed with migration:
  ```bash
  ./vendor/bin/sail artisan migrate
  ```
### 🔗 Accessing the App & Database:
- [🚀 Open Laravel App (localhost:8000)](http://localhost:8000)  
- [🛠️ Open phpMyAdmin (localhost:8088)](http://localhost:8088)

### 💡 Default phpMyAdmin Login Info
To check phpMyAdmin credentials, refer to your `.env`. file. Look for the following section:

```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=sail
DB_PASSWORD=password
```

## 🔎 Project Structure Overview

- `docker-compose.yml`  
  Contains configuration to run all required containers, including:
  - PHP (Laravel Sail)
  - MySQL
  - phpMyAdmin (optional for easier database access)

- `README.md`  
  Includes a complete guide on:
  - How to install and set up the project
  - Essential commands to manage the app
  - Troubleshooting tips

---

📌 **Note**:  
Make sure your MySQL version matches the one specified in the `.env` and `docker-compose.yml` files. For further references, check the official documentation:
- [Laravel Documentation](https://laravel.com/docs)
- [Docker Documentation](https://docs.docker.com)
- [MySQL Documentation](https://dev.mysql.com/doc)

Hope this tutorial helps! 😊
