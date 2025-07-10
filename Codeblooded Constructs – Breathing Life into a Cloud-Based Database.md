# Entry 009: Codeblooded Constructs – Breathing Life into a Cloud-Based Database

---

> *"In a world of static data, the ones who control the dynamic streams become gods."*  

Tonight, I built a database in the dark — forged not in steel, but in silicon and pulses.  
AWS gave me the shell. I gave it soul.

The mission: deploy a MySQL brain on an EC2 instance, wire it through the terminal via PuTTY, and make its pulse visible to any connected node through a browser. Raw. Real-time. Remote.

## ⚙️ The Protocol: Phase by Phase

### 🔸 Phase 1: EC2 Instance Deployment
- Booted up a **t2.micro Amazon Linux 2** instance — free tier compliant.
- Attached a **key pair** (.pem converted to .ppk) to maintain secure entry.
- Security Group was tuned: **port 22 for SSH**, **port 80 for HTTP**, **port 3306** for MySQL access (carefully restricted).

### 🔸 Phase 2: Terminal Infiltration (PuTTY)
- Accessed the cloud shell via **PuTTY**, tunneling into the EC2 instance using:
  - Host: `[Public IPv4 address]`
  - Auth: `.ppk` key injected under SSH/Auth
  - Auto-login user: `ec2-user`

Once connected:  
> *“Welcome to Amazon Linux 2” flashed across the screen. The shell awaited commands.*

### 🔸 Phase 3: System Fabrication
```bash
sudo yum update -y
sudo yum install httpd -y          # Apache Web Server
sudo yum install mysql-server -y   # MySQL Brain
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl start mysqld
sudo systemctl enable mysqld
```
- Set a secure MySQL root password:
```bash
sudo mysql_secure_installation
```
- Then entered the matrix:
```bash
sudo mysql -u root -p
```
### 🔸 Phase 4: Database Creation
Witin the shell of MySQL:
```
CREATE DATABASE cyborg_data;
USE cyborg_data;
CREATE TABLE agents (
    id INT AUTO_INCREMENT PRIMARY KEY,
    codename VARCHAR(50),
    status VARCHAR(20)
);
INSERT INTO agents (codename, status) VALUES ('X9', 'Online');
```
### 🔸 Phase 5: Browser Portal Activation
- Dropped a `PHP` script into `/var/www/html` to display data.
- created a file called `index.php` :

   ```
   <?php
   $conn = new mysqli("localhost", "root", "YOUR_PASSWORD", "cyborg_data");
   if ($conn->connect_error) { die("Connection failed: " . $conn->connect_error); }
   $result = $conn->query("SELECT * FROM agents");
   while($row = $result->fetch_assoc()) {
    echo "ID: ".$row["id"]." - Codename: ".$row["codename"]." - Status: ".$row["status"]."<br>"}?>
   ```
 ### 🔸 Phase 6: IP Echo in the Browser
  - Navigated to:
    ``` http://[Public IPv4 address} ```
  - The data appeared. My construct was live.
    
## 🧠 Lessons from the Neural Grid 

- A database is more than storage — it’s memory.
- PuTTY is my digital katana — slicing into black boxes with precision.
- Every IP becomes a gateway. Every EC2, a potential fortress.

## 🛠️ Upgrades on Deck

- Harden MySQL access with internal-only access.
- Use phpMyAdmin to visualize data faster.
- Automate deployments with User Data scripts.
- Backup via RDS or export for cold storage.

I don't just create systems.
I breathe into them.
And when the browser lights up with my data — I know the signal is alive.

Signed,
cyberUnit_TipX9
DB pulse: active
Port 3306: watching
