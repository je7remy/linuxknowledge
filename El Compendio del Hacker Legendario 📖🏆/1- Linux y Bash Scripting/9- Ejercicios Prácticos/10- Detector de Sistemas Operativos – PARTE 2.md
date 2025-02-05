#### **1.1. Comando de `ping` básico**

```bash
ping -c 1 192.168.118.161 | grep "ttl="
```

- **`ping -c 1`:** Envía un solo paquete ICMP a la dirección IP especificada.
- **`grep "ttl="`:** Filtra solo las líneas del resultado que contienen "ttl=", ya que es donde se indica el TTL del paquete.

#### **1.2. Extracción del TTL**

```bash
ping -c 1 192.168.118.161 | grep "ttl=" | awk '{print $6}'
```

- **`awk '{print $6}'`:** Toma la sexta columna de la salida (donde se encuentra `ttl=X`).

#### **1.3. Limpieza del valor de TTL**

```bash
ping -c 1 192.168.118.161 | grep "ttl=" | awk '{print $6}' | tr -d "ttl="
```

- **`tr -d "ttl="`:** Elimina el texto "ttl=" y deja solo el número del TTL.

---

### **2. Explicación del Script**

Este script determina si un host es accesible mediante `ping` y, basándose en el TTL del paquete, infiere el sistema operativo probable.

#### **Estructura del Script**

1. **Definición de colores para salida:**
    
    ```bash
    rojo_luminoso='\033[1;31m'
    verde_luminoso='\033[1;32m'
    cyan_luminoso='\033[1;36m'
    sin_color='\033[0m'
    ```
    
    - Define colores para resaltar el texto en la terminal.
    
1. **Entrada del usuario:**
    
    ```bash
    read -p "Introduce la direccion IP:  " IP
    ```
    
    - Solicita al usuario que introduzca una dirección IP.
    
1. **Verificación de conectividad:**
    
    ```bash
    if ping -c 1 $IP > /dev/null; then
        echo "El host es accesible"
    ```
    
    - Comprueba si el host responde al `ping`. Si no responde, muestra un mensaje de error.
    
1. **Obtención del TTL:**
    
    ```bash
    TTL=$(ping -c 1 $IP | grep "ttl=" | awk '{print $6}' | tr -d "ttl=")
    echo "El TTL es de $TTL"
    ```
    
    - Extrae el valor del TTL del resultado del comando `ping`.
    
1. **Identificación del sistema operativo:**
    
    ```bash
    if [ $TTL -gt 60 ] && [ $TTL -lt 70 ]; then
        echo -e "${verde_luminoso}El sistema operativo es Linux/Unix${sin_color}"
    elif [ $TTL -gt 100 ] && [ $TTL -lt 140 ]; then
        echo -e "${cyan_luminoso}El sistema operativo es Windows${sin_color}"
    else
        echo -e "${rojo_luminoso}No se puede determinar el sistema operativo${sin_color}"
    fi
    ```
    
    - Analiza el TTL para determinar el sistema operativo.
    
        - **Linux/Unix:** TTL típico entre 64 y 70.
        - **Windows:** TTL típico entre 128 y 140.
        - **Otros:** Muestra un mensaje indicando que no se puede determinar.
    
1. **Manejo de errores:**
    
    ```bash
    else
        echo -e "${rojo_luminoso}No tenemos conectividad con la IP${sin_color}"
    fi
    ```
    
    - Si no hay respuesta del host, muestra un mensaje indicando la falta de conectividad.

---

### **3. Implementación del Script Completo**

```bash
#!/bin/bash

rojo_luminoso='\033[1;31m'
verde_luminoso='\033[1;32m'
cyan_luminoso='\033[1;36m'
sin_color='\033[0m'

read -p "Introduce la direccion IP:  " IP

if ping -c 1 $IP > /dev/null; then
    echo "El host es accesible"
    TTL=$(ping -c 1 $IP | grep "ttl=" | awk '{print $6}' | tr -d "ttl=")
    echo "El TTL es de $TTL"

    if [ $TTL -gt 60 ] && [ $TTL -lt 70 ]; then
        echo -e "${verde_luminoso}El sistema operativo es Linux/Unix${sin_color}"
    elif [ $TTL -gt 100 ] && [ $TTL -lt 140 ]; then
        echo -e "${cyan_luminoso}El sistema operativo es Windows${sin_color}"
    else
        echo -e "${rojo_luminoso}No se puede determinar el sistema operativo${sin_color}"
    fi
else
    echo -e "${rojo_luminoso}No tenemos conectividad con la IP${sin_color}"
fi
```

---

### **4. Ejecución**

1. Guarda el script en un archivo, por ejemplo: `detectar_so.sh`.
2. Dale permisos de ejecución:
    
    ```bash
    chmod +x detectar_so.sh
    ```
    
3. Ejecuta el script:
    
    ```bash
    ./detectar_so.sh
    ```
    
4. Introduce una dirección IP cuando se solicite y observa los resultados.

---

**Flujo de ejecución:**

1. Establece colores para la salida
2. Pide al usuario una dirección IP
3. Realiza un ping de prueba

   - Si falla: muestra error en rojo

   - Si funciona:
   
      - Extrae el valor TTL de la respuesta
      
      - Compara el valor numérico:
      
        * 61-69 → Linux/Unix
        * 101-139 → Windows
        * Otros valores → Indeterminado

**Consideraciones importantes:**

1. Los valores TTL pueden verse afectados por:

   - Dispositivos de red intermedios (routers)
   - Configuraciones personalizadas del sistema
   - Distancia de red (número de saltos)

3. Valores TTL típicos desde origen:

   - Linux/Unix: 64
   - Windows: 128
   - Routers Cisco: 255

5. El script asume que hay solo 1 salto de red (lo cual es poco común en redes reales)

**Mejoras posibles:**

- Realizar múltiples intentos de ping para mayor precisión
- Considerar el número de saltos de red
- Agregar detección para otros sistemas operativos
- Usar técnicas más avanzadas como nmap para mayor precisión

Este método proporciona una estimación rápida pero básica del sistema operativo, útil para redes locales simples donde se conocen los saltos de red.

Este script es útil para pruebas rápidas y educativas, pero recuerda que la determinación de sistemas operativos basándose únicamente en TTL no es completamente precisa, ya que puede variar por configuraciones personalizadas.