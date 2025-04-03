
---

#Python #Colorama #Terminal #Colores #Estilos #Coding #Scripting #Tutorial

---

**1. Instalación de Colorama:**

- Se utiliza el comando `pip install colorama` para instalar el paquete **colorama** en el entorno de Python. Este paquete permite aplicar colores y estilos al texto mostrado en la terminal.
    

**2. Importación de módulos:**

- Se importa de **colorama** los módulos `Fore` (para colores de texto), `Back` (para colores de fondo) y `Style` (para estilos de texto, como brillante o tenue).
    

**3. Uso de colores y estilos en los `print`:**

- `print(Fore.RED + 'Este texto es rojo')`  
    Muestra el texto en color rojo.
    
- `print(Style.RESET_ALL + 'Reiniciamos color')`  
    Resetea todos los estilos y colores para que los siguientes textos se muestren sin el formato anterior.
    
- `print(Back.GREEN + 'Este texto tiene un fondo verde')`  
    Aplica un fondo verde al texto.
    
- Se alterna el uso de `Style.BRIGHT` para textos brillantes y `Style.DIM` para textos tenues.
    
- Se combinan estilos y colores, por ejemplo:  
    `print(Style.BRIGHT + Fore.YELLOW + 'Este es un texto en amarillo brillante (amarillo fosforito)')`  
    que muestra un texto brillante en color amarillo.
    
- Se utilizan también otros colores de texto (`Fore.YELLOW`, `Fore.RED`, `Fore.GREEN`, `Fore.BLUE`) y fondos (`Back.YELLOW`, `Back.MAGENTA`) para demostrar la variedad que ofrece **colorama**.
    

**4. Reseteo de estilos:**

- Cada vez que se usa `Style.RESET_ALL`, se reinician los colores y estilos para evitar que afecten al siguiente `print`.

# Código Completo:

````python
from colorama import Fore, Back, Style

  

print(Fore.RED + 'Este texto es rojo')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Back.GREEN + 'Este texto tiene un fondo verde')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Style.BRIGHT + 'Este texto es brillante')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Style.BRIGHT + Fore.YELLOW + 'Este es un texto en amarillo brillante (amarillo fosforito)')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Fore.YELLOW + 'Este es un texto en amarillo')

  
  

print(Fore.RED + 'Texto en rojo')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Fore.GREEN + 'Texto en verde')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Fore.BLUE + 'Texto en azul')

print(Style.RESET_ALL + 'Reiniciamos color')

  

print(Back.YELLOW + 'Fondo amarillo')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Back.MAGENTA + 'Fondo magenta')

print(Style.RESET_ALL + 'Reiniciamos color')

  
  

print(Style.DIM + 'Texto tenue')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Style.NORMAL + 'Texto normal')

print(Style.RESET_ALL + 'Reiniciamos color')

print(Style.BRIGHT + 'Texto brillante')

print(Style.RESET_ALL + 'Reiniciamos color')
`````

