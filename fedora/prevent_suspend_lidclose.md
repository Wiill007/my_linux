Encontré un foro en el cual se menciona [cómo evitar esto en Fedora 40](https://discussion.fedoraproject.org/t/prevent-suspend-when-lid-close-in-fedora-40/114278).

En resumen:
```sh
sudo mkdir /etc/systemd/logind.conf.d/
sudo cp /usr/lib/systemd/logind.conf /etc/systemd/logind.conf.d/
sudo nano /etc/systemd/logind.conf.d/logind.conf
```
Descomentar el flag de HandleSwitch y setearlo a ignore:
```conf
HandleLidSwitch=ignore.
```