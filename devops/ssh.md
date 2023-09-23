# SSH

## Introduction

SSH, which stands for "Secure Shell," is a cryptographic network protocol commonly used for secure remote system administration and file transfers. It operates on TCP port 22 by default, although this can be customized. SSH provides strong password authentication, public key authentication, and encrypted data communication between two computers connected through the internet.

[Official Website](https://www.openssh.com/)

[Wikipedia](https://en.wikipedia.org/wiki/Secure_Shell)

## Installation

```bash
sudo apt install ssh
```

To check if the server is alredy running.

```bash
systemctl status ssh
```

## SSH Key Generation

Public key authentication offers a more secure mechanism than password-based authentication. Two keys are generated: a public key, which anyone can see, and a private key, which is known only to the owner.

### SSH Key Generation Options

- **`-t` Algorithm Type**: Specifies the algorithm to use. RSA, DSA, ECDSA, or ED25519.
- **`-b` Bits**: The number of bits in the generated key, affecting encryption strength.
- **`-f` File**: The filename and path for the generated key.
- **`-C` Comment**: Label for the key.
- **`-N` Passphrase**: Additional layer of security for your SSH keys.

```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/id_custom_rsa -C "custom_label" -N "PassPhraseHere"
```

### Using `ssh-add` to Manage Keys

`ssh-add` adds SSH private keys to the `ssh-agent`, a background program that handles keys. This way, you only need to unlock the key once.

#### Options

- **Default Key**: `ssh-add` with no arguments adds the default key.
- **Custom Key**: `ssh-add /path/to/key`
- **List Fingerprints**: `ssh-add -l`
- **Remove All Keys**: `ssh-add -D`
- **Remove Specific Key**: `ssh-add -d /path/to/key`
- **Set Timeout**: `ssh-add -t 3600 /path/to/key`

```bash
ssh-add -t 3600 ~/.ssh/id_custom_rsa
```

### Transferring Keys to Remote Servers

Use `ssh-copy-id` to install your public key in a remote server's `~/.ssh/authorized_keys`.

```bash
ssh-copy-id username@remote_host
```

## Commands and Usage Scenarios

### Basic and Advanced Connections

Connect with or without custom port specification.

```bash
ssh username@hostname
ssh -p 2222 username@hostname
```

### Port Forwarding and Tunneling

Forward local ports to remote ports or the reverse.

```bash
ssh -L 8080:localhost:80 username@remote_host
```

### File Transfers: SCP and SFTP

SCP and SFTP protocols for secure file transfers.

```bash
scp local_file username@remote_host:/path/
sftp username@remote_host
```

## Advanced Configurations

### SSH Config File

Utilize SSH config files for more complicated setups and frequent connections.

```bash
Host alias_name
    HostName actual_host_name
    User username
    Port port_number
```

### X11 Forwarding

For GUI-based applications over SSH.

```bash
ssh -X username@remote_host
```

## Best Practices

- Favor SSH keys over passwords.
- Keep your system and SSH packages updated.
- Use firewalls to limit access.
- Use `Fail2Ban` or similar to prevent brute-force attacks.
