# Resume-Install-VM-in-Manjaro
Instalacion de Oracle Virtualbox en Manjaron linux, resumido, copia la siguiente funcion


```shell
function oracle_vm_install() {
  sudo pacman -Syu

  # Usar este modulo en caso de la instalacion comun de Manjaro
  sudo pacman -Syu virtualbox linux65-virtualbox-host-modules 
  sudo vboxreload

  # Comprobar que todo este bien
  vboxmanage --version

  # Configuraciones extras
  sudo gpasswd -a $USER vboxusers

  # Solución de Problemas del Huésped (Guest):
  sudo pacman -Syu virtualbox-guest-utils linux54-virtualbox-guest-modules

  sudo modprobe vboxguest vboxvideo vboxsf
  sudo systemctl enable --now vboxservice.service

  sudo usermod -aG vboxsf ${USER}
  sudo mkdir /media
  sudo chmod 755 /media
}
```
