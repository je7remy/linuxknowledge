1. **echo**
   ```bash
   echo
   echo "Hola Mundo"
   echo "Hola\nMundo"
   echo -e "Hola\nMundo"
   ```
   - `echo` simplemente imprime una línea en blanco.
   - `echo "Hola Mundo"` imprime "Hola Mundo" en una línea.
   - `echo "Hola\nMundo"` imprime "Hola\nMundo" literalmente, sin interpretar el `\n` como una nueva línea.
   - `echo -e "Hola\nMundo"` interpreta `\n` como una nueva línea, por lo que imprime "Hola" en una línea y "Mundo" en la siguiente.

2. **Script 1**
   ```bash
   #!/bin/bash

   echo -n "Este texto se va a imprimir sin la nueva linea, "
   echo "Suspuestamente la nuevea linea"
   ```
   - `echo -n "Este texto se va a imprimir sin la nueva linea, "` imprime el texto sin añadir una nueva línea al final.
   - `echo "Suspuestamente la nuevea linea"` imprime el texto en la misma línea, ya que `echo` anterior tenia el argumento `-n`.

3. **Script 2**

```bash
#!/bin/bash

echo -ne "Este texto se va a imprimir sin la nueva linea,\n "
echo "Suspuestamente la nuevea linea"
```

- `echo -ne "Este texto se va a imprimir sin la nueva linea,\n "`: Aquí, `-n` evita que `echo` añada una nueva línea al final del texto, y `-e` permite la interpretación de secuencias de escape como `\n`, que representa una nueva línea. Así que el texto "Este texto se va a imprimir sin la nueva linea," se imprime seguido de una nueva línea debido a `\n`.
- `echo "Suspuestamente la nuevea linea"`: Este comando imprime "Suspuestamente la nuevea linea" en una nueva línea, ya que `echo` por defecto añade una nueva línea al final del texto.

Entonces, el resultado final sería:
```
Este texto se va a imprimir sin la nueva linea,
 Suspuestamente la nuevea linea
```

