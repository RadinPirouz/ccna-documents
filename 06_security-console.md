
# 🔒 Console & Password Security

## Basic Console Password

```bash
line console 0
password 123
login
````

## Encrypted Console Password

```bash
service password-encryption
line console 0
password 123
login
enable secret 123
```

## SHA-256 Encrypted Console + Enable Password

```bash
service password-encryption
line console 0
password 123
login
enable algorithm-type sha-256 secret 123
```

## Local User Authentication with SHA-256

```bash
service password-encryption
line console 0
login local
enable algorithm-type sha-256 secret 123
username radin algorithm-type sha-256 secret 123
```
