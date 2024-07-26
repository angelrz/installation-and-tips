# INSTALAR QUARTUS LITE 23.1

## Ejecutar el instalador

```bash
sudo chmod +x *.run
```

```bash
sudo ./*.run
```

- Seleccionar para descargar e instalar, sugiero la siguiente ruta: **/home/USUARIO/intelFPGA_lite/23.1std**  
- **Saltar** creación del ejecutable y el primer lanzamiento

## Crear variables de entorno

Abrir el archivo bashrc con nano

```bash
nano ~/.bashrc  
```

Escribir al final del archivo lo siguiente

```bash
export PATH=/home/angel/intelFPGA_lite/23.1std/quartus/bin:${PATH}

QUARTUS_ROOTDIR_OVERRIDE=/home/angel/intelFPGA_lite/23.1std/quartus
export QUARTUS_ROOTDIR_OVERRIDE

QUARTUS_64BIT=1
export QUARTUS_64BIT
```
  
Salir para reinciar terminal y escribir **quartus** para verificar que aparezca

```text
quartus: error while loading shared libraries: libprotobuf.so.14: cannot open shared object file: No such file or direct  
```

```bash
sudo chmod -R go=u-w intelFPGA_lite/
```
  
**Puedes seguir el siguiente [PDF sobre Quartus](https://mil.ufl.edu/3701/docs/quartus/Quartus19.1_install_on_Linux.pdf) para JTAG**

- Descargar el libtag <https://marsohod.org/downloads/category/16?download=178>
- Descomprimir y ejecutar copiar el directorio:

```bash
cp libjtag_hw_mbftdi-blaster.so ~/intelFPGA_lite/23.1std/quartus/linux64  
```

## Driver USB Blaster

[Cable II Driver on Linux Systems](https://www.intel.com/content/www/us/en/docs/programmable/683719/current/installing-the-driver-on-linux-systems.html)
  
Crear o abrir archivo **51-usbblaster.rules**

```bash
sudo nano /etc/udev/rules.d/51-usbblaster.rules
```
  
Puede o no aparecer esto:

```text
SUBSYSTEM=="usb",ENV{DEVTYPE}=="usb_device",ATTR{idVendor}=="0403",ATTR{idProdu>
10",MODE="0666",RUN+="/usr/sbin/rmmod ftdi_sio"
```
  
Modificar por la [Sugerencia en Intel Community](https://community.intel.com/t5/Intel-Quartus-Prime-Software/Quartus-II-JTAG-Server-Error-Code-89/td-p/162221) o bien:

```text
# USB-Blaster
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="09fb", ATTRS{idProduct}=="6001", MODE="0666", SYMLINK+="usbblaster/%k"  
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="09fb", ATTRS{idProduct}=="6002", MODE="0666", SYMLINK+="usbblaster/%k"  
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="09fb", ATTRS{idProduct}=="6003", MODE="0666", SYMLINK+="usbblaster/%k"  
  
# USB-Blaster II
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="09fb", ATTRS{idProduct}=="6010", MODE="0666", SYMLINK+="usbblaster2/%k"  
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", ATTRS{idVendor}=="09fb", ATTRS{idProduct}=="6810", MODE="0666", SYMLINK+="usbblaster2/%k"
```
  
O bien, ocupar el archivo de este [repositorio](https://github.com/GoComputing/QuartusInstallerUbuntu/tree/master/files) de Github.

## Crear ejecutable (icono)

```bash
sudo nano /usr/share/applications/quartus.desktop
```

Agregar las siguientes propiedades:

```text
[Desktop Entry]
Name=Quartus Prime
Comment=Lite Edition (23.1)
Version=1.0
Type=Application
Exec=/home/angel/intelFPGA_lite/23.1std/quartus/bin/quartus -desktop
Icon=/home/angel/intelFPGA_lite/23.1std/quartus/adm/quartusii.png
Terminal=false
```

Reiniciar PC sí no aparece el ejecutable
