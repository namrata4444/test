
***

# 📘 The Complete Linux & LEMP Stack Guidebook
**From Beginner to Advanced User**

---

## 1. Introduction

### 1.1. What is Linux?
Linux is an open-source, Unix-like operating system kernel first released by Linus Torvalds in 1991. Combined with a suite of software from the GNU project, it forms a complete operating system, often referred to as GNU/Linux. It is renowned for its stability, security, and flexibility, powering everything from embedded devices and smartphones (Android) to the vast majority of the world's servers and supercomputers.

### 1.2. The Linux Philosophy
*   **Everything is a file:** Hardware, directories, and processes are represented as files.
*   **Small, single-purpose programs:** Programs that do one thing and do it well.
*   **Chain programs together:** The output of one program can be the input for another (piping).
*   **Avoid captive user interfaces:** Prefer command-line scripts for automation.
*   **Store data in text files:** Text files are universal and easy to process.

### 1.3. What is a LEMP Stack?
The LEMP stack is a popular set of open-source software used to serve web applications.
*   **L** - **Linux**: The operating system (e.g., Ubuntu, CentOS).
*   **E** - **Nginx** (engine-x): The high-performance web server.
*   **M** - **MySQL/MariaDB**: The relational database management system.
*   **P** - **PHP/Python**: The programming language used for application logic.

This guide will take you from your first Linux commands to deploying a fully functional LEMP stack.

---

## 2. Linux Fundamentals: The Command Line

### 2.1. File System Navigation
| Command | Description | Example |
| :--- | :--- | :--- |
| `pwd` | **P**rint **W**orking **D**irectory | `pwd` → `/home/user` |
| `ls` | **L**i**s**t directory contents | `ls -la` |
| `cd` | **C**hange **D**irectory | `cd /var/www` |
| `cd ~` or `cd` | Go to your home directory | `cd ~` |
| `cd ..` | Move up one directory level | `cd ..` |
| `cd -` | Go to the previous directory | `cd -` |

### 2.2. File Operations
| Command | Description | Example |
| :--- | :--- | :--- |
| `touch` | Create a new, empty file | `touch index.html` |
| `cat` | Con**cat**enate, used to view file content | `cat config.txt` |
| `cp` | **C**o**p**y files and directories | `cp file.txt backup/` |
| `mv` | **M**o**v**e or rename files and directories | `mv old.txt new.txt` |
| `rm` | **R**e**m**ove files and directories | `rm file.txt` (use `-r` for directories) |
| `mkdir` | **M**a**k**e **dir**ectory | `mkdir new_project` |
| `rmdir` | **R**e**m**ove empty **dir**ectory | `rmdir old_dir` |

### 2.3. File Viewing and Editing
| Command | Description |
| :--- | :--- |
| `less` | View file content page by page (press `q` to quit). |
| `head` | Output the first 10 lines of a file. |
| `tail` | Output the last 10 lines of a file. Great for logs (`tail -f logfile` to follow). |
| `nano` | Simple, user-friendly text editor. |
| `vim` / `vi` | Powerful, modal text editor. Steeper learning curve. |

### 2.4. Getting Help
| Command | Description |
| :--- | :--- |
| `man <command>` | View the **man**ual page for a command (e.g., `man ls`). |
| `<command> --help` | Most commands have a built-in help option. |
| `whatis <command>` | Gives a one-line description of the command. |
| `which <command>` | Shows the full path of the shell command. |

---

## 3. Intermediate Linux System Administration

### 3.1. User and Permission Management
Linux is a multi-user system. Permissions control access.
*   **Ownership:** Every file and process is owned by a **user** and a **group**.
*   **Permissions:** Defined for the **user**, **group**, and **others** (**u**/**g**/**o**).
    *   `r` - Read (4)
    *   `w` - Write (2)
    *   `x` - e**X**ecute (1)

| Command | Description | Example |
| :--- | :--- | :--- |
| `sudo` | **S**uper**U**ser **DO**. Execute a command as the root user. | `sudo apt update` |
| `chmod` | **Ch**ange **mod**e (permissions) | `chmod 755 script.sh` (rwxr-xr-x) |
| `chown` | **Ch**ange **own**ership | `chown www-data:www-data /var/www/` |
| `whoami` | Print effective userid | `whoami` |
| `passwd` | Change user password | `passwd` |

### 3.2. Process Management
| Command | Description | Example |
| :--- | :--- | :--- |
| `ps` | **P**rocess **S**tatus | `ps aux` (view all running processes) |
| `top` / `htop` | Dynamic, real-time view of running processes (`htop` is enhanced). | `htop` |
| `kill` | Terminate a process by its **PID** | `kill 1234` |
| `killall` | Terminate processes by name | `killall nginx` |
| `systemctl` | Control **systemd** services | `systemctl status nginx` |

### 3.3. Package Management with `apt` (Debian/Ubuntu)
| Command | Description |
| :--- | :--- |
| `sudo apt update` | Fetches the list of available packages from configured sources. |
| `sudo apt upgrade` | Installs available upgrades for all currently installed packages. |
| `sudo apt install <pkg>` | Installs a package. | `sudo apt install nginx` |
| `sudo apt remove <pkg>` | Removes a package but keeps configuration files. |
| `sudo apt purge <pkg>` | Removes a package and its configuration files. |
| `sudo apt autoremove` | Removes packages automatically installed that are no longer needed. |

### 3.4. Networking Commands
| Command | Description | Example |
| :--- | :--- | :--- |
| `ping` | Test connectivity to a host | `ping google.com` |
| `curl` | Transfer data from or to a server | `curl -I http://example.com` |
| `wget` | Non-interactive network downloader | `wget http://example.com/file.zip` |
| `ssh` | **S**ecure **Sh**ell, log into a remote machine | `ssh user@server_ip` |
| `ifconfig` / `ip a` | Display network interface information | `ip a` |
| `netstat` | Network statistics | `netstat -tulnp` (show listening ports) |

---

## 4. Advanced Linux Power Tools

### 4.1. Text Processing and Filtering
| Command | Description | Example |
| :--- | :--- | :--- |
| `grep` | **G**lobal **R**egular **E**xpression **P**rint. Search text. | `grep "error" log.txt` |
| `find` | Search for files in a directory hierarchy. | `find / -name "*.log" -type f` |
| `sort` | Sort lines of text files. | `sort file.txt` |
| `uniq` | Report or omit repeated lines. | `sort file.txt \| uniq` |
| `awk` | Pattern scanning and processing language. | `awk '{print $1}' file.txt` |
| `sed` | **S**tream **Ed**itor for filtering and transforming text. | `sed 's/foo/bar/g' file.txt` |

### 4.2. Redirection and Piping
*   **`>`** : Redirect standard output (overwrite). `ls > list.txt`
*   **`>>`** : Redirect standard output (append). `echo "new" >> list.txt`
*   **`2>`** : Redirect standard error.
*   **`|`** : **Pipe**. Take the output of one command as input to the next.
    *   `cat log.txt | grep "error" | sort | uniq`

### 4.3. Archiving and Compression
| Command | Description | Example |
| :--- | :--- | :--- |
| `tar` | **T**ape **Ar**chive. Bundle files together. | |
| | Create: `-cvf` | `tar -cvf archive.tar /folder/` |
| | Extract: `-xvf` | `tar -xvf archive.tar` |
| `gzip` / `gunzip` | Compress/Decompress using LZ77. `.gz` format. | `gzip file.txt` -> `file.txt.gz` |
| `tar` + `gzip` | Common combination. Use `-z` flag. | `tar -czvf archive.tar.gz /folder/` |

### 4.4. System Monitoring
| Command | Description |
| :--- | :--- |
| `df -h` | **D**isk **F**ree. Show disk usage in human-readable format. |
| `du -sh` | **D**isk **U**sage. Summarize total size of a directory. |
| `free -h` | Display amount of free and used memory in the system. |
| `uptime` | Show how long the system has been running and load average. |

### 4.5. Introduction to Shell Scripting
A shell script is a text file containing a sequence of commands.
**Example Script: `backup.sh`**
```bash
#!/bin/bash
# This is a comment
# Define variables
BACKUP_DIR="/backups"
SOURCE_DIR="/var/www/html"

# Create a timestamped archive
tar -czf $BACKUP_DIR/backup-$(date +%Y%m%d-%H%M).tar.gz $SOURCE_DIR

# Print success message
echo "Backup of $SOURCE_DIR completed successfully!"
```
**To run it:**
```bash
chmod +x backup.sh  # Make it executable
./backup.sh         # Execute it
```

---

## 5. LEMP Stack Setup Guide (Ubuntu 22.04 LTS)

### 5.1. Step 1: Prerequisites
*   A server running **Ubuntu 22.04**.
*   A non-root user with `sudo` privileges.
*   A firewall configured with `ufw`.

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install ufw -y
sudo ufw allow OpenSSH
sudo ufw enable
```

### 5.2. Step 2: Install Nginx
Nginx is a high-performance web server that will handle HTTP requests.

```bash
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx # Start on boot
sudo ufw allow 'Nginx Full' # Allow HTTP (80) and HTTPS (443)
```
**Verify:** Open your web browser and navigate to your server's IP address. You should see the Nginx welcome page.

### 5.3. Step 3: Install MySQL
MySQL is a database management system used to store and manage your website's data.

```bash
sudo apt install mysql-server -y
sudo systemctl start mysql
sudo systemctl enable mysql
```
**Secure Installation:**
```bash
sudo mysql_secure_installation
```
Follow the prompts to:
1.  Set a strong root password (if not using auth_socket).
2.  Remove anonymous users.
3.  Disallow remote root login.
4.  Remove test database.
5.  Reload privilege tables.

### 5.4. Step 4: Install PHP
PHP-FPM (FastCGI Process Manager) processes PHP code. We also install core extensions.

```bash
sudo apt install php-fpm php-mysql php-cli php-curl php-zip php-mbstring php-xml php-gd -y
```
Check the version: `php -v`

### 5.5. Step 5: Configure Nginx to Use PHP Processing
1.  **Create a server block (virtual host):**
    ```bash
    sudo nano /etc/nginx/sites-available/your_domain
    ```
2.  **Paste the following configuration,** replacing `your_domain` with your actual domain or server IP.
    ```nginx
    server {
        listen 80;
        server_name your_domain www.your_domain;
        root /var/www/your_domain;
        index index.php index.html index.htm;

        location / {
            try_files $uri $uri/ =404;
        }

        location ~ \.php$ {
            include snippets/fastcgi-php.conf;
            fastcgi_pass unix:/var/run/php/php8.1-fpm.sock; # Confirm version (php8.1, php7.4, etc.)
        }

        location ~ /\.ht {
            deny all;
        }
    }
    ```
3.  **Enable the site:**
    ```bash
    sudo ln -s /etc/nginx/sites-available/your_domain /etc/nginx/sites-enabled/
    # Test the configuration for syntax errors
    sudo nginx -t
    # If successful, restart Nginx
    sudo systemctl restart nginx
    ```
4.  **Create the web root directory and test file:**
    ```bash
    sudo mkdir /var/www/your_domain
    sudo chown -R $USER:$USER /var/www/your_domain
    echo "<?php phpinfo(); ?>" > /var/www/your_domain/info.php
    ```
**Verify:** Navigate to `http://your_domain/info.php`. You should see the PHP information page. **Delete this file afterwards** for security: `sudo rm /var/www/your_domain/info.php`

---

## 6. LEMP Stack Management & Usage

### 6.1. Service Management
| Task | Command |
| :--- | :--- |
| Check Nginx Status | `sudo systemctl status nginx` |
| Restart PHP-FPM | `sudo systemctl restart php8.1-fpm` |
| Stop MySQL | `sudo systemctl stop mysql` |
| View Nginx Logs | `sudo tail -f /var/log/nginx/error.log` |

### 6.2. Database Management (MySQL)
*   **Login as root:**
    ```bash
    sudo mysql
    # or
    mysql -u root -p
    ```
*   **Common MySQL Commands:**
    ```sql
    -- Show all databases
    SHOW DATABASES;

    -- Create a new database and user for your application
    CREATE DATABASE app_db;
    CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'strong_password';
    GRANT ALL PRIVILEGES ON app_db.* TO 'app_user'@'localhost';
    FLUSH PRIVILEGES;

    -- Switch to a database
    USE app_db;

    -- Show tables in the current database
    SHOW TABLES;
    ```

### 6.3. Deploying a PHP Application (e.g., WordPress)
1.  Download and extract the application to your web root (`/var/www/your_domain`).
2.  Set correct ownership: `sudo chown -R www-data:www-data /var/www/your_domain`
3.  Create a MySQL database and user for the application (as shown above).
4.  Access your domain in a browser and follow the application's installation wizard.

---

## 7. Security and Optimization

### 7.1. Basic Server Security
*   **Firewall (UFW):** Ensure only necessary ports are open (SSH, HTTP, HTTPS).
*   **Fail2Ban:** Scan log files and ban IPs showing malicious signs.
    ```bash
    sudo apt install fail2ban -y
    ```
*   **Disable Root SSH Login:** Edit `/etc/ssh/sshd_config` and set `PermitRootLogin no`.
*   **Keep Systems Updated:** Regularly run `sudo apt update && sudo apt upgrade`.

### 7.2. SSL/TLS with Let's Encrypt
Secure your site with free HTTPS certificates.
```bash
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d your_domain -d www.your_domain
```
Certbot will automatically edit your Nginx config and reload it. Certificates auto-renew.

### 7.3. Nginx Optimizations
*   **Worker Processes:** In `/etc/nginx/nginx.conf`, set `worker_processes auto;` to match CPU cores.
*   **Gzip Compression:** Enable gzip in `/etc/nginx/nginx.conf` to reduce file sizes.
*   **Caching:** Configure browser caching for static assets (images, CSS, JS).

---

This guide provides a solid foundation. The world of Linux is vast—continue exploring by reading `man` pages, following tutorials, and most importantly, practicing.
