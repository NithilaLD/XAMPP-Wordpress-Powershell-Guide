# PowerShell Command Reference

This document contains all PowerShell commands used throughout the guide, organized by section.

---

# 1. XAMPP Installation

## Open PowerShell as Administrator

```powershell
powershell
```

---

## Download XAMPP

```powershell
Start-Process "https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/8.0.30/xampp-windows-x64-8.0.30-0-VS16-installer.exe/download"
```

---

## Install XAMPP

```powershell
cd C:\

C:\xamppsetup.exe --unattendedmodeui minimal --mode unattended
```

---

## Verify Installation

```powershell
cd C:\xampp

dir
```

---

## Uninstall XAMPP (if installation failed)

```powershell
cd C:\

C:\xampp\uninstall.exe
```

---

# 2. Apache Service Installation

## Navigate to Apache

```powershell
cd C:\xampp\apache\bin
```

---

## Verify Apache Files

```powershell
dir

dir ap*
```

---

## Install Apache Service

```powershell
cd ..

dir ap*

C:\xampp\apache\apache_installservice.bat
```

---

## Check Apache Service

```powershell
Get-Service a*
```

---

## Stop Apache Service

```powershell
Stop-Service Apache2.4
```

---

## Verify Service Status

```powershell
Get-Service a*
```

---

# 3. MySQL Service Installation

## Navigate to MySQL

```powershell
cd C:\xampp\mysql\bin
```

---

## Install MySQL Service

```powershell
.\mysqld -install
```

---

## Verify Service

```powershell
Get-Service m*
```

---

## Stop MySQL

```powershell
Stop-Service MySQL
```

---

## Verify Status

```powershell
Get-Service m*
```

---

# 4. WordPress Installation

## Go to C Drive

```powershell
cd C:\
```

---

## Get Local IP

```powershell
ipconfig
```

---

## Check Apache Service

```powershell
Get-Service a*
```

---

## Start Apache

```powershell
Start-Service Apache2.4
```

---

## Check MySQL

```powershell
Get-Service m*
```

---

## Start MySQL

```powershell
Start-Service MySQL
```

---

## Open XAMPP Dashboard

```powershell
Start-Process http://localIP
```

---

## Open phpMyAdmin

```powershell
Start-Process http://localIP/phpmyadmin
```

---

## Edit Apache Configuration

```powershell
notepad C:\xampp\apache\conf\extra\httpd-xampp.conf
```

---

## Restart Apache

```powershell
Restart-Service Apache2.4
```

---

# 5. Download WordPress

```powershell
Start-Process "https://wordpress.org/latest.zip"
```

---

## Copy WordPress ZIP

```powershell
cp C:\wordpress.zip C:\xampp\htdocs\wordpress.zip
```

---

## Verify

```powershell
cd C:\xampp\htdocs

ls
```

---

## Extract WordPress

```powershell
Expand-Archive -LiteralPath C:\xampp\htdocs\wordpress.zip -DestinationPath C:\xampp\htdocs\yourname
```

---

## Launch WordPress

```powershell
Start-Process http://localIP/yourname/wordpress
```

---

# 6. PHP Upgrade

## Download PHP

```powershell
cd C:\

Start-Process https://windows.php.net/download/
```

---

## Rename Old PHP

```powershell
Rename-Item -Path "C:\xampp\php" -NewName "C:\xampp\php_old"

ls C:\xampp
```

---

## Create New PHP Folder

```powershell
New-Item -ItemType Directory -Path "C:\xampp\php"

ls C:\xampp
```

---

## Extract PHP

```powershell
Expand-Archive -LiteralPath C:\php.zip -DestinationPath C:\xampp\php

ls C:\xampp\php
```

---

## Copy php.ini

```powershell
cp C:\xampp\php\php.ini-development C:\xampp\php\php.ini

ls C:\xampp\php
```

---

## Edit php.ini

```powershell
notepad C:\xampp\php\php.ini
```

---

## Edit Apache PHP Module

```powershell
notepad C:\xampp\apache\conf\extra\httpd-xampp.conf
```

---

## Restart Apache

```powershell
Restart-Service Apache2.4
```

---

## Verify PHP

```powershell
Start-Process "http://localIP/dashboard/phpinfo.php"
```

---

# 7. phpMyAdmin Upgrade

## Download phpMyAdmin

```powershell
Start-Process https://www.phpmyadmin.net/downloads/
```

---

## Rename Existing Folder

```powershell
Rename-Item -Path "C:\xampp\phpMyAdmin" -NewName "C:\xampp\phpMyAdmin_old"

ls C:\xampp
```

---

## Extract ZIP

```powershell
Expand-Archive -Path "C:\phpmyadmin.zip" -DestinationPath "C:\xampp\phpmyadmin_extracted" -Force
```

---

## Create New Folder

```powershell
New-Item -Path "C:\xampp\phpMyAdmin" -ItemType Directory -Force
```

---

## Copy Files

```powershell
Copy-Item "C:\xampp\phpmyadmin_extracted\$(Get-ChildItem 'C:\xampp\phpmyadmin_extracted' -Directory | Select-Object -First 1)\*" "C:\xampp\phpMyAdmin" -Recurse -Force
```

---

## Delete Temporary Folder

```powershell
Remove-Item "C:\xampp\phpmyadmin_extracted" -Recurse -Force
```

---

## Restore Configuration

```powershell
Copy-Item "C:\xampp\phpMyAdmin_old\config.inc.php" "C:\xampp\phpMyAdmin" -Force
```

---

## Create tmp Directory

```powershell
New-Item -Path "C:\xampp\phpMyAdmin\tmp" -ItemType Directory -Force
```

---

## Grant Permissions

```powershell
icacls "C:\phpMyAdmin\tmp" /grant "Everyone:(OI)(CI)M" /T
```

---

## Restart Apache

```powershell
Restart-Service Apache2.4
```

---

## Verify phpMyAdmin

```powershell
Start-Process "http://localIP/phpmyadmin"
```

---

# 8. Stop Services

## Stop Apache

```powershell
Stop-Service Apache2.4

Get-Service a*
```

---

## Stop MySQL

```powershell
Stop-Service MySQL

Get-Service m*
```

---

# 9. Start WordPress Later

## Start Apache

```powershell
Start-Service Apache2.4
```

---

## Start MySQL

```powershell
Start-Service MySQL
```

---

## Open WordPress

```powershell
Start-Process "http://localhost/yourname/wordpress"
```

---

## Open WordPress Admin

```powershell
Start-Process "http://localhost/yourname/wordpress/wp-login.php"
```

---

# 10. Shutdown After Work

```powershell
Stop-Service Apache2.4

Stop-Service MySQL
```
