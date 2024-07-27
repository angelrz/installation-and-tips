# Instalar MATLAB R2024A en Linux Debian y derivados

## Descargar el instalador de MATLAB

Desde [MATLAB](https://la.mathworks.com/downloads/), seleccionar la versión y dar clic en descargar.

## Descomprimir el instalador

Puede ser desde el explorador de archivos o terminal con el comando

```bash
unzip matlab_R2024a_Linux.zip
```

## Abrir el instalador

Después de descomprimir, abrir la carpeta que apareció en la terminal y ejecutar el siguiente comando

```bash
sudo ./install
```

## Pasos siguientes

Agregar cuenta, selec software, finalizar, puedes ver el [Video](https://www.youtube.com/watch?v=KCDG_SCDcaY) del minuto 1:00 al 2:00

Seleccionar la ruta por defecto: **/usr/local/MATLAB/R2023b**

> [!WARNING]
> Recuerda la ruta, es indispensable para tus variables de entorno

## Ejecutar MATLAB

Al tratar de ejecutar la orden **matlab** en terminal te aparecerá un error, hace falta la variable de entorno

## Variables de entorno

Abrir con nano el archivo bashrc en terminal

```bash
sudo nano ~/.bashrc
```

Y escribir la variable de entorno

```bash
export PATH=/usr/local/MATLAB/R2023b/bin:${PATH}
```

## Crear ejecutable

Descarga una imagen, renombrala como **icono-matlab.png**, abre terminal y pega:

```bash
sudo cp /home/angel/Descargas/icono-matlab.png /usr/local/MATLAB/R2023b/resources/coreui/matlab/icono-matlab.png
```

Ahora, crea el ejecutable:

```bash
sudo nano /usr/share/applications/matlab.desktop
```

Y pega lo siguiente:

```text
[Desktop Entry]
Name=Matlab
Comment=R2023b
Version=1.0
Type=Application
Exec=/usr/local/MATLAB/R2023b/bin/matlab -desktop
Icon=/usr/local/MATLAB/R2023b/resources/coreui/matlab/icono-matlab.png
Terminal=false
```

> [!TIP]
> También puedes visitar este [Blog](https://linux.how2shout.com/how-to-install-matlab-in-ubuntu-22-04/)
