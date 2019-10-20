#!/bin/bash
# Última actualización: 19/10/2019
cd /
# Se descarga Koofr
wget https://app.koofr.net/dl/apps/linux64
cd /usr/local/
echo 'Se va a instalar en /usr/local/...'
read -p "Ingresa el nombre del directorio principal de instalacion, si no existe se creará: " DIRINST
if [ -d $DIRINST ];
	then
		echo 'El directorio ya existe...'
		echo '>>> Ingresando...'
		cd $DIRINST
	else
		echo 'El directorio no existe...'
		echo 'Creando directorio...'
		mkdir $DIRINST
		echo 'Directorio creado...'
		echo '>>> Ingresando...'
		cd $DIRINST
fi
sleep 2
mv /linux64 /usr/local/$DIRINST
tar xzvf linux64
#
#App a Menú
cd /usr/share/applications/
touch koofr.desktop
echo '[Desktop Entry]' > koofr.desktop
echo 'Version=xxx' >> koofr.desktop
echo 'Name=Koofr' >> koofr.desktop
echo 'Comment=One storage for all' >> koofr.desktop
echo 'Exec=/usr/local/'$DIRINST'/koofr/storagegui' >> koofr.desktop
echo 'Icon=/usr/local/'$DIRINST'/koofr/icon.png' >> koofr.desktop
echo 'Categories=Network;' >> koofr.desktop
echo 'Terminal=false' >> koofr.desktop
echo 'Type=Application' >> koofr.desktop
cd /usr/local/$DIRINST/koofr/
#
#Remove
touch remove.sh
echo "#!/bin/bash" > remove.sh
echo "echo '------------------------------'" >> remove.sh
echo "echo 'Removiendo...'" >> remove.sh
echo "echo -ne '[===>                                    ]( 8.33%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[=========>                              ](16.66%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[============>                           ](24.99%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[===============>                        ](33.32%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[==================>                     ](41.65%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[=====================>                  ](49.98%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[========================>               ](58.31%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[===========================>            ](66.64%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[==============================>         ](74.97%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[=================================>      ](83.30%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[====================================>   ](91.64%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '[=======================================>](100.00%)\r';sleep 0.2" >> remove.sh
echo "echo -ne '\n'" >> remove.sh
echo 'cd /' >> remove.sh
echo 'rm -rf /usr/share/applications/koofr.desktop' >> remove.sh
echo 'rm -rf /usr/local/'$DIRINST'/koofr/' >> remove.sh
echo 'rm -rf /home/*/.koofr/' >> remove.sh
echo "echo 'Completado!'" >> remove.sh
echo "echo '------------------------------'" >> remove.sh
echo 'exit' >> remove.sh
chmod 744 remove.sh
#
#README
touch README.txt
echo 'Koofr' > README.txt
echo 'Idioma=es_MX' >> README.txt
echo 'Version=xxx' >> README.txt
echo 'Arquitectura=64-bit' >> README.txt
echo 'Esta es una instalación no invasiva.' >> README.txt
echo 'Para desinstalar ejecute el fichero remove.sh como root.' >> README.txt
echo '' >> README.txt
echo 'https://koofr.eu/' >> README.txt
echo '' >> README.txt
echo 'xaxlm' >> README.txt
#
# Limpieza
cd /
echo '------------------------------'
echo 'Limpiando...'
echo -ne '[===>                                    ]( 8.33%)\r';sleep 0.2
echo -ne '[=========>                              ](16.66%)\r';sleep 0.2
echo -ne '[============>                           ](24.99%)\r';sleep 0.2
echo -ne '[===============>                        ](33.32%)\r';sleep 0.2
echo -ne '[==================>                     ](41.65%)\r';sleep 0.2
echo -ne '[=====================>                  ](49.98%)\r';sleep 0.2
echo -ne '[========================>               ](58.31%)\r';sleep 0.2
echo -ne '[===========================>            ](66.64%)\r';sleep 0.2
echo -ne '[==============================>         ](74.97%)\r';sleep 0.2
echo -ne '[=================================>      ](83.30%)\r';sleep 0.2
echo -ne '[====================================>   ](91.64%)\r';sleep 0.2
echo -ne '[=======================================>](100.00%)\r';sleep 0.2
echo -ne '\n'
rm -rf /usr/local/$DIRINST/linux64
echo 'Completado!'
echo '------------------------------'
exit
