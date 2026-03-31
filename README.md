
<p align="center">
  <img src="https://raw.githubusercontent.com/TEAMBCS/AUTH-NEXUS/main/Image/auth-nexus-logo.png" width="500">
</p>

<h1 align="center">AUTH NEXUS</h1>

<p align="center">
<b>Advanced Brute Force Attack Testing Framework</b>
</p>

<p align="center"><b>
A professional multi-protocol brute force attack testing tool built for security researchers and penetration testers.</b>
</p>

---
## Dependencies

![aiohttp](https://img.shields.io/badge/aiohttp-async%20http-green)
![aiohttp-socks](https://img.shields.io/badge/aiohttp--socks-proxy%20support-orange)
![rich](https://img.shields.io/badge/rich-terminal%20ui-purple)
![beautifulsoup4](https://img.shields.io/badge/beautifulsoup4-html%20parser-yellow)
![lxml](https://img.shields.io/badge/lxml-fast%20xml%20parser-blue)
![asyncssh](https://img.shields.io/badge/asyncssh-ssh%20client-red)
![uvloop](https://img.shields.io/badge/uvloop-fast%20async%20loop-green)
![urllib3](https://img.shields.io/badge/urllib3-http%20client-lightgrey)
![pyOpenSSL](https://img.shields.io/badge/pyOpenSSL-ssl%20support-blue)
![License](https://img.shields.io/badge/license-GPLv3-blue.svg)
![Version](https://img.shields.io/badge/Version-1.0%20-yellow)

---

# 🔐 Auth Nexus

**Auth Nexus** is a powerful brute force attack testing framework designed for security professionals and penetration testers.

It supports multiple protocols such as:

- HTTP / HTTPS
- SSH
- FTP
- SMTP

The tool is designed with **high performance asynchronous architecture**, **smart login detection**, **automatic CSRF handling**, and **memory-safe credential streaming**.

Auth Nexus provides a modern **TUI (Terminal User Interface)** for easy configuration and monitoring.

---

# 🚀 Key Features

### Multi Protocol Support
Supports authentication testing for multiple protocols:

- HTTP / HTTPS login forms
- SSH authentication
- FTP authentication
- SMTP authentication

---

### Smart Web Login Detection

- Automatic username/password field detection
- Automatic CSRF token detection
- Cookie session handling
- Smart redirect analysis

---

### High Performance Engine

- Asynchronous architecture
- Multi-threaded request handling
- High RPS processing
- Optimized network operations

---

### Memory Safe Credential Streaming

Large credential lists can be used safely.

Example:

```

rockyou.txt (140MB+)

````

The tool reads credentials **line-by-line** instead of loading everything into memory.

---

### Proxy & Stealth Support

Auth Nexus supports:

- HTTP proxies
- SOCKS4 / SOCKS5 proxies
- Randomized requests
- Delay control
- Stealth headers

---

### Professional TUI Interface

Modern terminal interface with:

- live logs
- progress tracking
- RPS monitoring
- ETA calculation
- valid credential display

---

# ⚙️ Installation && Requirement Setup

### Requirements

- Python 3.10+
- Linux / Termux / macOS


```bash
pkg update && pkg upgrade
pkg install python3 -y
pkg install git -y
git clone https://github.com/TEAMBCS/AUTH-NEXUS.git
cd AUTH-NEXUS
chmod +x *
chmod 777 *
pip install -r auth-nexus.txt
python3 auth-nexus.py
```

---

# 🧠 Supported Attack Modes

Auth Nexus supports three major credential attack strategies.

---

## Cluster Bomb

Tests **every username with every password**

Example

```
User1 : Pass1
User1 : Pass2
User1 : Pass3
User2 : Pass1
User2 : Pass2
User2 : Pass3
```

Best for:

```
Multiple usernames × password list
```

---

## Pitchfork

Runs username and password lists **in parallel**

Example

```
User1 : Pass1
User2 : Pass2
User3 : Pass3
```

Best for:

```
Paired credential lists
```

---

## Battering Ram

Uses the **same value for both username and password**

Example

```
admin : admin
test : test
user : user
```

Best for:

```
Default credential testing
```

---

# 📖 User Manual

### Target Configuration

Target can be provided as:

Single URL

```
http://target.com/login
```

Or URL list

```
targets.txt
```

Example formats:

```
http://site.com/login
ssh://192.168.1.10:22
ftp://127.0.0.1:21
smtp://mail.server.com:587
```

---

### Credentials Input

Auth Nexus supports both single credentials and wordlists.

Single credential:

```
User : admin
Pass : password123
```

Credential lists:

```
users.txt
passwords.txt
```

---

### HTTP Form Example

Example login form configuration:

```
/login:user=^USER^&pass=^PASS^:F=Invalid or /login:user=^USER^&pass=^PASS^:S=Success
```
Explanation

| Part      | Meaning              |
| --------- | -------------------- |
| /login    | form path            |
| ^USER^    | username placeholder |
| ^PASS^    | password placeholder |
| F=Invalid | failure message      |
| S=Success | success meassage     |

Examples :➤ 
Cpanel : ```/login/:user=^USER^&pass=^PASS^:F=invalid```

Wp : ```/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In:F=Invalid username```

---

### 🧠 Auto Param Feature

The Auto Param system analyzes the target request and automatically 
extracts possible authentication parameters such as:

• username fields  
• password fields  
• token parameters  
• login form inputs  

This helps speed up authentication testing without requiring 
manual parameter configuration.
---

# 📊 Tool Architecture

```
Auth Nexus
│
├── Engine
│   ├── HTTP Module
│   ├── SSH Module
│   ├── FTP Module
│   └── SMTP Module
│
├── Smart Detection
│   ├── Parameter Detection
│   ├── CSRF Detection
│   └── Cookie Handling
│
├── Credential System
│   ├── Wordlist Streaming
│   ├── Cluster Bomb
│   ├── Pitchfork
│   └── Battering Ram
│
├── Networking
│   ├── Async Requests
│   ├── Proxy Support
│   └── Retry System
│
└── Interface
    ├── TUI Dashboard
    ├── Live Logs
    ├── Progress Tracking
    └── Results Display
```

---

# 📈 Statistics Display

Auth Nexus provides real-time attack statistics:

| Metric   | Description              |
| -------- | ------------------------ |
| Attempts | Total attempts           |
| RPS      | Requests per second      |
| ETA      | Estimated time remaining |
| Hits     | Valid credentials found  |

---

# 📁 Project Structure

```
AUTH-NEXUS
│
├── auth-nexus.py #main tool
├── auth-nexus.txt #requirements
├── auth-nexus-ua.json #User agent list
├── passlist.txt #A common password list
├── README.md
│
├── Image
|   ├── tool-img-1.png #Tool Image 
|   ├── tool-img-2.png #Tool Image
│   └── auth-nexus-logo.png #logo image
│
├── AUTH-NEXUS-CSS
|   ├── UI.css #main UI css
|   ├── about.css #about info css
│   ├── attack-ui.css #attack panel ui css
│   └── app.css #app css
│
└── output
    └── success.txt
```

---
## 📸 Screenshots

<p align="center">
  <img src="https://raw.githubusercontent.com/TEAMBCS/AUTH-NEXUS/main/Image/tool-img-1.png" width="45%" alt="Screenshot 1">
  &nbsp;&nbsp;
   <img src="https://raw.githubusercontent.com/TEAMBCS/AUTH-NEXUS/main/Image/tool-img-2.png" width="45%" alt="Screenshot 2">
  &nbsp;&nbsp;


</p>

---

# 🛡 Security Notice

This tool is developed for:

* **Cybersecurity research**
* **penetration testing**
* **authorized security assessments**

Unauthorized usage against systems without permission is illegal.

---

# 👨‍💻 Developer

```
Owner : TEAM BCS
Developer : BLACK ZER0
```

---

# 📜 License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)**.


```
Licensed under the GNU General Public License v3.0 (GPLv3).

This license allows users to use, modify and distribute the software, 
but any modified version must also be released under the same GPLv3 license.
```

---

# ⭐ Support

If you like the project consider giving a **star on GitHub**.

```
Stay secure.
Stay ethical.
```

---

