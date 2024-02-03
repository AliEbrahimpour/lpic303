lpic303

- [1. GPG](#1-gpg)
  - [1.1. manage GPG Key](#11-manage-gpg-key)
    - [1.1.1. generate gpg key](#111-generate-gpg-key)
    - [1.1.2. encrypt file:](#112-encrypt-file)
    - [1.1.3. decrypt file:](#113-decrypt-file)
  - [1.2. export public key](#12-export-public-key)
  - [1.3. list of public keys](#13-list-of-public-keys)
- [2. shred](#2-shred)
  - [2.1. shred or Delete file without recovery !](#21-shred-or-delete-file-without-recovery-)
- [3. OPENSSL (Self-Signed Certificate)](#3-openssl-self-signed-certificate)
- [4. IPTABLES](#4-iptables)
  - [4.1. List Entries in iptables](#41-list-entries-in-iptables)
  - [4.2. Set Default Policy for INPUT to ACCEPT](#42-set-default-policy-for-input-to-accept)
  - [4.3. ACCEPT Connections From a Single IP Address](#43-accept-connections-from-a-single-ip-address)
  - [4.4. DROP Connections for an IP Range](#44-drop-connections-for-an-ip-range)
  - [4.5. REJECT OUTBOUND Connections for an IP on a Specific Port (SSH)](#45-reject-outbound-connections-for-an-ip-on-a-specific-port-ssh)
  - [4.6. DROP All OUTGOING Connections; ALLOW only CONNECTIONS to 192.168.1.1](#46-drop-all-outgoing-connections-allow-only-connections-to-19216811)
  - [4.7. Saving Changes Made to iptables](#47-saving-changes-made-to-iptables)
  - [4.8. Clearing All the Rules](#48-clearing-all-the-rules)
  - [4.9. Deleting Individual Rules](#49-deleting-individual-rules)
- [refrence:](#refrence)



# 1. GPG

## 1.1. manage GPG Key

### 1.1.1. generate gpg key
```
gpg --full-generate-key
```


### 1.1.2. encrypt file:
```
echo "ali" > ali.txt
```
```
gpg -c --cipher-algo AES256 a.txt
```
```
gpp -s -e ali.txt
```
### 1.1.3. decrypt file:
```
gpg -d ali2.txt.gpg > a.txt
```

## 1.2. export public key
```
gpg --export -a > ali.pub
gpg --export -a > ali.pub
```

## 1.3. list of public keys
```
https://keyserver.ubuntu.com/
```


# 2. shred
## 2.1. shred or Delete file without recovery !
```
shred -n 20 -u -v ali.txt
```

# 3. OPENSSL (Self-Signed Certificate)
```
 cd /etc/httpd/ && mkdir ssl && cd ssl/
 openssl genrsa 2048 private.key
 openssl req -new-key private.key > request.csr
 openssl req -text-in request.esr
 openssl rsa -in private.key pubout (This is how you can extract the Public Key from Private Key)
 openssl x589-tn request.csr -out cert.crt-req-signkey private.key-days 365[root@localhost]s openssl x509 text in cert.crt
 openssl x589 pubkey -noout in cert.crt (This is how you can extract Public key from Certificate)Now set them in your Apache configurations and check this out that it works well.
```

# 4. IPTABLES
## 4.1. List Entries in iptables
```
iptables -L
```


## 4.2. Set Default Policy for INPUT to ACCEPT
```
iptables --policy INPUT ACCEPT
```


## 4.3. ACCEPT Connections From a Single IP Address
```
iptables -A INPUT -s 10.10.10.10 -j ACCEPT
```


## 4.4. DROP Connections for an IP Range
```
iptables -A INPUT -s 10.10.10.0/24 -j DROP
```


## 4.5. REJECT OUTBOUND Connections for an IP on a Specific Port (SSH)
```
iptables -A OUTPUT -p tcp --dport ssh -s 10.10.10.10 -j REJECT
```



## 4.6. DROP All OUTGOING Connections; ALLOW only CONNECTIONS to 192.168.1.1
```
iptables --policy OUTPUT DROP
iptables -A OUTPUT -d 192.168.1.1 -j ACCEPT
```


## 4.7. Saving Changes Made to iptables
```
iptables-save
```

## 4.8. Clearing All the Rules
```
iptables -F
```


## 4.9. Deleting Individual Rules
```
iptables -D INPUT -s 127.0.0.1 -p tcp -dport 111 -j ACCEPT 
```
```
iptables -D INPUT 4
```




# refrence:
```
https://github.com/Borosan/lpic3book

```