# raf-repo

Personal rolling pacman repository for x86_64.

## Import the signing key

Download the repository public key and verify its fingerprint before importing it:

```sh
curl -LO https://github.com/rozeraf/raf-repo/releases/download/x86_64/rozeraf-repo-key.asc
gpg --show-keys --with-fingerprint rozeraf-repo-key.asc
```

Expected fingerprint:

```text
8180 ACCD 03D3 45F7 681D  2D37 DDCE 5997 AEB9 743D
```

Add the key to pacman's keyring and locally trust it:

```sh
sudo pacman-key --add rozeraf-repo-key.asc
sudo pacman-key --lsign-key 8180ACCD03D345F7681D2D37DDCE5997AEB9743D
```

## Configure pacman

Add the following section to `/etc/pacman.conf`:

```ini
[raf]
SigLevel = Required DatabaseRequired
Server = https://github.com/rozeraf/raf-repo/releases/download/$arch
```

Then synchronize the package databases:

```sh
sudo pacman -Syy
```
