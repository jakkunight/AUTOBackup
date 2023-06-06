# AUTOBackup
## ¿Qué es AUTOBackup?
Es un script que realiza una copia de seguridad de máquinas virtuales creadas en entornos PROXMOX VE (v7.4+) 
en volúmenes compartidos mediante SAMBA, siendo el entorno PROXMOX el cliente SMB.
## Requisitos:
Debe tener intalado PROXMOX VE 7.3 o superior. Debería funcionar en versiones más viejas, pero no hay pruebas realizadas en dichas versiones.  
Debe contar con la utilidad VZDUMP y el paquete "cifs-utils". 
Si no tiene instalado este último, puede hacerlo vía APT:
```Sell
	apt install cifs-utils
```
## Instalación y uso
Clone el repositorio mediante el CLI de Git:
```Shell
	git clone https://github.com/jakkunight/AUTOBackup
```
Si no cuenta con el CLI de Git, puede instalarlo con el siguiente comando:
```Shell
	apt install git
```
O bien descargue el código en un archivo .zip desde GitHub y descomprima el mismo en la carpeta que más le guste. 
Una vez que tenga su versión de AUTOBackup, deberá configurar el servicio de crontab para que el programa se ejecute de forma automática 
y realice sus labores en forma automática.
Para ello, ejecute el siguiente comando a continuación:  
```Shell
	crontab -e
```
Al hacerlo, si es la primera vez que configura crontab, se le preguntará que editor de texto desea utilizar para llevar a cabo la acción. 
Si ya posee experiencia utilizando alguno de ellos, elija el de su preferencia. En caso contrario, le recomiendo nano debido a su sencillez.  
Una vez seleccionado el editor, escriba la frecuencia y tiempo con que debe ser ejecutado AUTOBackup. Luego escriba la ruta absoluta hasta el 
archivo AUTOBackup. Guarde el archivo y salga del editor.  
A continuación, ejecute el siguiente comando para reiniciar cron:
```Shell
	systemctl restart cron
```
O bien:
```Shell
	service cron restart
```
¡Y listo! Debería ejecutarse el script de manera automática a la hora especificada y con la frecuencia deseada.
## Configuración
AUTOBackup cuenta con una configuración por defecto. Si desea ajustarla, puede modificar el archivo AUTOBackup a su conveniencia.  
En cualquier caso, deberá contar con los siguientes datos:
+ ID de la máquina virtual a respaldar (Por defecto 100).
+ IP del servidor SAMBA al cual copiar el respaldo (Por defecto 127.0.0.1).
+ Un alias para poder motar el volúmen SMB de manera local (Por defecto "smb_backups").
+ El nombre o ruta de la carpeta compartida en el servidor SAMBA al cual se copiará el respaldo (Por defecto "shared").
## Reporte de bugs
Ante cualquier problema, puede abrir un "issue" en este repositorio de GitHub.
## Contribuyentes
- Jakku Night (Autor del script)
- Net Company (Contribución financiera)


Si desea apoyar el proyecto, puede contribuir mediante un "pull request" o GitHub Sponsors.
