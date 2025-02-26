#!/bin/bash

# Colores para salida
blueColour="\e[0;34m\033[1m"
yellowColour="\e[0;33m\033[1m"
redColour="\e[0;31m\033[1m"
endColour="\e[0m"

# Función para manejar la salida con Ctrl+C
function ctrl_c(){
    echo -e "\n\n${redColour}[!] Saliendo...${endColour}\n"
    exit 1
}

# Capturar señal Ctrl+C
trap ctrl_c INT

# Buscar archivos .txt y guardar en una variable
txt_files=$(find / -type f -name "*.txt" 2>/dev/null)

# Verificar si se encontraron archivos
if [ -z "$txt_files" ]; then
    echo -e "\n${redColour}[!] No se encontraron archivos .txt.${endColour}\n"
else
    echo -e "\n${yellowColour}[+]${endColour} ${blueColour}Archivos .txt encontrados:${endColour}\n"
    echo "$txt_files"
fi
