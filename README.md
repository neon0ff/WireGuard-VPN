# WireGuard VPN Server
### Для начала обновим систему и установим "curl"
```bash
sudo apt update && sudo apt upgrade
```
```bash
sudo apt install curl
```
### Скачаем скрипт и сделаем его выполняемымм
```bash
curl -O https://raw.githubusercontent.com/neon0ff/WireGuard-VPN/main/wireguard-install.sh
```
```bash
chmod +x wireguard-install.sh
```
###  Выполним скрипт. Ответим на вопросы, заданные сценарием, и он позаботится обо всем остальном
```bash
./wireguard-install.sh
```
## Для удалеие VPN сервера или удаления / добавления пользователей просто запустите скрипт повтороно и выберете нужное действие

# WireGuard VPN Client


## Linux

### Войдем по SSH на Linux сервер, после входа в систему проверим, обновлена ли машина, выполнив следующую команду
```bash
sudo apt-get update && sudo apt-get upgrade
```
### Теперь установим WireGuard, выполнив следующую команду
```bash
sudo apt-get install wireguard
```
### После этого создаём или редактируем файл конфигурации клиента, в следующем каталоге
<sub>Для каждого клиента создается сфой конфигурационный файл на сервере с VPN<sub>
```bash
sudo nano /etc/wireguard/wg0.conf
```
### Файл должен иметь примерно такой ввид:
```
[Interface]
PrivateKey = yB5NqkYqs2T2H9iiCz7HcCB0PAY3qi3lEajDjyQMUFw=
Address = 10.66.66.2/32,fd42:42:42::2/128
DNS = 8.8.8.8,8.8.4.4

[Peer]
PublicKey = FTPXDMI3CmxspFonpMnx6Y/s3m3mYYmAtKjqGSnH4AM=
PresharedKey = aoDndDZ/9fB+bgKPW95HyNa1xpfaqapSuU5zRpV/We5M=
Endpoint = 123.456.78.910:53781
AllowedIPs = 0.0.0.0/0,::/0
```
### Для запуска соединения введем следующую команду
```bash
sudo wg-quick up wg0
```
### Нас выкенет с сервера т.к. сервер будет принимать соедение с тунеля и нужно  подключиться к VPN и потом к нашему серверу используя внутренний ip адресс в нашем случае 10.66.66.2
```bash
ssh user@10.66.66.2
```
### Для отключения соединения введем эту команду
```bash
sudo wg-quick down wg0
```

## Windows/IOS

### Скачиваем файл конфигурации для клиента с сервера через FileZilla или аналоги
### Скачиваем оофицильный клиент для Windows/IOS [тут](https://www.wireguard.com/install/)
### После заппускаем клиент нажимаем на "Импорт туннелей из файла"
![image](https://github.com/neon0ff/WireGuard-VPN/assets/128789652/07a83d52-deaa-488c-8650-82e4d1496e1f)
### После чего выбираем наш конфиг и добавляем его
![image](https://github.com/neon0ff/WireGuard-VPN/assets/128789652/1cd2e120-a5cf-40da-bdeb-a64e4fd4e3de)
### После чего мы можем подключиться
