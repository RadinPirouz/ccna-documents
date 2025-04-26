# Cisco CLI Commands – Console Password Configuration

## Create Console Password Without Any Authentication
Set a basic console password:
```bash
line console 0
password 123
login
```

---

## Create Console Password with Password Encryption
Encrypt the console password using Cisco's built-in encryption:
```bash
service password-encryption
line console 0
password 123
login
```

Set a secure enable password:
```bash
enable secret 123
```

---

## Create Console Password with Custom Encryption (SHA-256)
Encrypt the enable secret using SHA-256:
```bash
service password-encryption
line console 0
password 123
login
enable algorithm-type sha-256 secret 123
```

---

## Create Console Password with Custom Encryption and Local User Authentication
Set a console password, use local username/password authentication with SHA-256 encryption:
```bash
service password-encryption
line console 0
login local
enable algorithm-type sha-256 secret 123
username radin algorithm-type sha-256 secret 123
```
