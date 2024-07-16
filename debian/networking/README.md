# Networking en Debian.
Como Raspian se basa en Debian también nos resulta útil para este. De hecho también para ubuntu pero lo he dejado aparte por netplan.

## Setear IP estática:
Nos basamos en esta [web](https://itslinuxfoss.com/set-up-static-ip-address-debian-12-linux/). Pasos:
1. Ir al directorio /etc/network/interfaces.d
> Nota: Por defecto en /etc/network/interfaces se incluyen todos los archivos de interfaces.d
2. Crear archivos según nuestro interés. En mi caso uno para cada interfaz. Por ejemplo los siguientes:
Para eth0 (eth0.conf):
```
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
```
Mientras que para wlan0 (wlan0.conf):
```
auto wlan0
iface wlan0 inet static
address 192.168.0.20
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8
```
> **IMPORTANTE:** No está soportado añadir comentarios utilizando el carácter *#* como en Python.
3. El servicio se actualiza solo a no ser que hayamos añadido algún interfaz virtual, por lo tanto, el comando *sudo systemctl restart networking* no debe ser ejecutado a no ser que tratemos con este último caso.
