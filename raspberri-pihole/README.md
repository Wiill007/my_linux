# Guía de configuración:

## PiHole
Bastante simple. Referirse al repositorio de [PiHole](https://github.com/pi-hole/pi-hole) y seguir la guía de instalación en la primera aproximación.

## Post install instructions
Seguir las [instrucciones post-install](https://docs.pi-hole.net/main/post-install/) para activar dhcp en el mismo PiHole.


## Static IP
Hay que configurar ahora la **IP estática** en la raspberry. Para ello se [sigue esta guía de bookworm](https://www.abelectronics.co.uk/kb/article/31/set-a-static-ip-address-on-raspberry-pi-os-bookworm) con la cual podemos setear la ip estática. Lo dejo copiado aquí por si acaso:

### Step 1:

Before we can begin you will need to find the name of the network interface you want to set as static. You can do this by running the following command in a terminal to display a list of available network interfaces.

```sh
sudo nmcli -p connection show
```

You should see a listing like the one below.

```sh
======================================
  NetworkManager connection profiles
======================================
NAME                UUID                                  TYPE      DEVICE
----------------------------------------------------------------------------
Wired connection 1  bd220d18-7d6a-36a5-9820-4f67de2c01fc  ethernet  eth0
mywifi              2359440b-8991-4c86-a905-b011dced4587  wifi      wlan0
lo                  c29ba7c5-98ff-4fa0-8d8e-06b30b8ec384  loopback  lo
```

The default name for the wired ethernet connection for English locales is "Wired connection 1". This name may be different if you use another language; for example, the German name will be "Kabelgebundene Verbindung 1". To find the correct connection name, look for the row with a Type of "ethernet".

The WiFi connection will typically have the name of your WiFis SSID. If your Raspberry Pi uses different names for the network connections or you would like to change your WiFi IP address, replace "Wired connection 1" with the correct name in the following commands. 

 

### Step 2:

Now we know the name of the network connection we want to update, we can send three commands to set the new IP address, Gateway and DNS (domain name server) server.
```sh
sudo nmcli c mod "Wired connection 1" ipv4.addresses 10.0.0.220/24 ipv4.method manual

sudo nmcli con mod "Wired connection 1" ipv4.gateway 10.0.0.1

sudo nmcli con mod "Wired connection 1" ipv4.dns 10.0.0.1
```

## Step 3:
Activar [unbound](https://docs.pi-hole.net/guides/dns/unbound/) si se desea


## Wireguard
Seguir la [guía de PiHole](https://docs.pi-hole.net/guides/vpn/wireguard/overview/)