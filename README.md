# WireGuard-VPN Server
### Для начала обновим систему и установим "cirl"
```bash
sudo apt update && sudo apt upgrade
```
```bash
sudo apt install curl
```
### Скачаем скрипт и сделаем его выполняемымм.
```bash
curl -O https://raw.githubusercontent.com/neon0ff/WireGuard-VPN/main/wireguard-install.sh
```
```bash
chmod +x wireguard-install.sh
```
###  Выполним скрипт. Ответим на вопросы, заданные сценарием, и он позаботится обо всем остальном.
```bash
./wireguard-install.sh
```
