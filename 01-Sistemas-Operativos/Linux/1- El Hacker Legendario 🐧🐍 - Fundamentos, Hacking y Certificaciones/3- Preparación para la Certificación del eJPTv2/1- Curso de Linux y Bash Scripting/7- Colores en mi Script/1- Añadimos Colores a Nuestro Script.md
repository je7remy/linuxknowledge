En Bash, puedes usar códigos de escape ANSI para asignar colores a variables:

```bash
#!/bin/bash

# Colores asignados a variables con su nombre
red='\033[0;31m'
green='\033[0;32m'
blue='\033[0;34m'
yellow='\033[0;33m'
cyan='\033[0;36m'
magenta='\033[0;35m'
white='\033[0;37m'
black='\033[0;30m'

# Estilos adicionales
bold='\033[1m'
underline='\033[4m'
reset='\033[0m' # Para restablecer el color

# Uso de las variables de color
echo -e "${red}Este texto es rojo.${reset}"
echo -e "${green}Este texto es verde.${reset}"
echo -e "${blue}Este texto es azul.${reset}"
echo -e "${yellow}Este texto es amarillo.${reset}"
echo -e "${cyan}Este texto es cian.${reset}"
echo -e "${magenta}Este texto es magenta.${reset}"
echo -e "${white}Este texto es blanco.${reset}"
echo -e "${black}Este texto es negro (puede no ser visible en algunos fondos).${reset}"

# Ejemplo con estilos
echo -e "${bold}${blue}Texto azul en negrita.${reset}"
echo -e "${underline}${green}Texto verde subrayado.${reset}"
```

### Explicación:

1. **Códigos de escape ANSI**:
    
    - `\033`: Introducción del código ANSI.
    - `[0;XXm`: Código del color o estilo, donde `XX` define el color o atributo (31 para rojo, 32 para verde, etc.).
    - `reset`: `\033[0m` para restablecer los colores y estilos al valor predeterminado.
2. **Colores básicos**:
    
    - **30**: Negro
    - **31**: Rojo
    - **32**: Verde
    - **33**: Amarillo
    - **34**: Azul
    - **35**: Magenta
    - **36**: Cian
    - **37**: Blanco
3. **Estilos adicionales**:
    
    - **1**: Negrita.
    - **4**: Subrayado.
4. **Uso de `reset`**: Asegúrate de usar `${reset}` al final de cada línea para evitar que los colores se propaguen.
    

### Ejecución:

Guarda el código en un archivo, por ejemplo, `colores.sh`, y ejecútalo:

```bash
bash colores.sh
```


---

En Bash, los colores luminosos (también conocidos como colores de negrita o brillantes) se activan usando códigos ANSI con formato especial. A continuación te muestro cómo utilizarlos:

### Formato básico de colores en Bash:

```bash
echo -e "\e[1;31mTexto en rojo brillante\e[0m"
```

### Explicación:

- `\e` o `\033`: Inicio de una secuencia de escape.
- `[1`: Código para negrita/brillo.
- `;31`: Código del color (en este caso, rojo).
- `m`: Final de la secuencia de estilo.
- `\e[0m`: Restablece el color y el formato al predeterminado.

### Colores básicos y sus códigos:

|Código|Color|Código negrita/brillante|Color brillante|
|---|---|---|---|
|30|Negro|1;30|Gris oscuro|
|31|Rojo|1;31|Rojo brillante|
|32|Verde|1;32|Verde brillante|
|33|Amarillo|1;33|Amarillo brillante|
|34|Azul|1;34|Azul brillante|
|35|Magenta|1;35|Magenta brillante|
|36|Cian|1;36|Cian brillante|
|37|Blanco|1;37|Blanco brillante|

### Ejemplo completo:

```bash
echo -e "\e[1;31mRojo brillante\e[0m"
echo -e "\e[1;32mVerde brillante\e[0m"
echo -e "\e[1;33mAmarillo brillante\e[0m"
echo -e "\e[1;34mAzul brillante\e[0m"
echo -e "\e[1;35mMagenta brillante\e[0m"
echo -e "\e[1;36mCian brillante\e[0m"
echo -e "\e[1;37mBlanco brillante\e[0m"
```

### Script completo:

```bash
#!/bin/bash

# =======================================================================================
# Script de demostración de colores en Bash
# Autor: Jeremy Jose de la Cruz Perez
# Descripción: Este script muestra el uso de diferentes colores y estilos en la terminal.
# =======================================================================================

# ========================
# Definición de colores
# ========================
# Colores básicos
red='\033[0;31m'       # Rojo
green='\033[0;32m'     # Verde
blue='\033[0;34m'      # Azul
yellow='\033[0;33m'    # Amarillo
cyan='\033[0;36m'      # Cian
magenta='\033[0;35m'   # Magenta
white='\033[0;37m'     # Blanco
black='\033[0;30m'     # Negro (puede ser invisible en fondos oscuros)

# Colores brillantes
bright_red='\033[1;31m'       # Rojo brillante
bright_green='\033[1;32m'     # Verde brillante
bright_yellow='\033[1;33m'    # Amarillo brillante
bright_blue='\033[1;34m'      # Azul brillante
bright_magenta='\033[1;35m'   # Magenta brillante
bright_cyan='\033[1;36m'      # Cian brillante
bright_white='\033[1;37m'     # Blanco brillante

# Estilos adicionales
bold='\033[1m'         # Negrita
underline='\033[4m'    # Subrayado
reset='\033[0m'        # Restablecer color y estilo

# ========================
# Inicio del script
# ========================

# Mensaje de bienvenida
echo -e "${bold}${cyan}Bienvenido al script de demostración de colores en Bash${reset}"
echo -e "${underline}Este script muestra texto en diferentes colores y estilos.${reset}\n"

# Mostrar colores básicos
echo -e "${red}Este texto es rojo.${reset}"
echo -e "${green}Este texto es verde.${reset}"
echo -e "${blue}Este texto es azul.${reset}"
echo -e "${yellow}Este texto es amarillo.${reset}"
echo -e "${cyan}Este texto es cian.${reset}"
echo -e "${magenta}Este texto es magenta.${reset}"
echo -e "${white}Este texto es blanco.${reset}"
echo -e "${black}Este texto es negro (puede no ser visible en algunos fondos).${reset}\n"

# Mostrar colores brillantes
echo -e "${bright_red}Rojo brillante${reset}"
echo -e "${bright_green}Verde brillante${reset}"
echo -e "${bright_yellow}Amarillo brillante${reset}"
echo -e "${bright_blue}Azul brillante${reset}"
echo -e "${bright_magenta}Magenta brillante${reset}"
echo -e "${bright_cyan}Cian brillante${reset}"
echo -e "${bright_white}Blanco brillante${reset}\n"

# Mensaje de despedida
echo -e "${bold}${green}¡Gracias por usar este script!${reset}"

# ========================
# Fin del script
# ========================
```

### Nota:

El comando `echo -e` es necesario para que interprete los códigos de escape en Bash. Si estás escribiendo un script, asegúrate de incluir siempre el comando de restablecimiento (`\e[0m`) después de los colores para evitar que el formato afecte otras partes de la terminal.