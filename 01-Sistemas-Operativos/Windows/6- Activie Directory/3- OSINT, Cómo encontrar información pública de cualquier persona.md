
**By:  Zunderrub**, Rubén Zaragoza Abad

---

#ctf  #cybersecurity  #hacker  #tryhackme  #redteam  #pentesting  #hacking #wordpress  #metasploitframework  #metasploit  #parrotos  #kalilinux  #Zunderrub #exploit #vulnerability #cms

---

¡Hola a todos! Hoy voy a narrar cómo investigaría a una persona desde cero usando herramientas de OSINT (Open Source Intelligence).

---

### **Paso 1: Partir de una foto**
Todo empieza con una foto, Mi objetivo es descubrirlo todo sobre él, así que usen una imagen como punto de partida.

---

### **Paso 2: Reconocimiento facial para identificar a la persona**
Decido usar herramientas de reconocimiento facial para ver si puedo encontrar más fotos de este tipo y, con suerte, su nombre.

- **PimEyes**: Subo la foto a PimEyes, una herramienta que busca coincidencias en internet. Tras aceptar los términos, me muestra varias imágenes similares. Veo fotos en periódicos como *Libertad Digital* y menciones junto a nombres como Aznar y Zapatero. "¡Ajá!", pienso, "este tío debe ser un político español". La versión gratuita me da pistas, pero con la de pago podría tener más detalles. Por ahora, me basta con saber que es alguien relevante en política.

- **FaceCheck.id**: Pruebo también FaceCheck.id, pero no me impresiona. Me da resultados parecidos a PimEyes, aunque menos útiles sin pagar. Lo descarto por ahora.

- **Google Images**: Entonces, se me ocurre usar algo más básico: Google Images. Subo la foto y ¡boom! Google me dice que es Mariano Rajoy, un político español que fue presidente del gobierno. Además, me salen artículos y más fotos suyas. "Vale, ya tengo su nombre", me digo, emocionado. ¡Primer éxito!

---

### **Paso 3: Buscar en LinkedIn para datos personales**
Ahora que sé que se llama Mariano Rajoy, voy a buscar su perfil en LinkedIn para ver qué más puedo descubrir sobre su vida.

- Entro a LinkedIn, escribo "Mariano Rajoy" en la barra de búsqueda y encuentro su perfil. Dice que vive en "Madrid y alrededores", que estudió en la Universidad de Santiago de Compostela (lo que me hace pensar que es gallego), y que fue presidente del gobierno de España, entre otros cargos. "Interesante", pienso, "esto ya me da una idea de quién es".

- Luego, instalo una extensión llamada **SignalHire** en mi navegador. La uso en su perfil y, ¡sorpresa!, me da un número de teléfono y un correo electrónico con dominio @hotmail.com. No estoy seguro de si es su número personal o uno asociado a su trabajo político, pero es un dato jugoso. Por ética, decido no compartirlo públicamente si estuviera grabando esto.

---

### **Paso 4: Verificar el número con Truecaller**
Quiero asegurarme de que el número que conseguí es real, así que voy a usar Truecaller.

- Abro Telegram, busco el bot de **Truecaller**, y le envío el número con el prefijo +34 (por ser España). El bot me responde: "Mariano Rajoy". También me dice la operadora telefónica y si ha sido reportado como spam. "¡Funciona!", exclamo. Esto confirma que el número está asociado a él. Me siento como detective privado.

---

### **Paso 5: Herramientas de OSINT en la terminal**
Ahora quiero ir más allá y usar herramientas más técnicas desde mi terminal. Me pongo en modo hacker (sin hacer nada ilegal, claro, todo es público).

- **Mr. Holmes**: Esta herramienta busca información basada en correos o teléfonos. Como no tengo su correo real, invento uno: "marianorajoy@gmail.com". Lo ingreso, elijo la opción de búsqueda por email, y Mr. Holmes valida si existe y busca datos. Me encuentra posibles cuentas asociadas (como Spotify o Twitter) y sugiere buscar más en Google o Yandex. "Qué pasada", pienso, mientras miro el reporte que me genera.

- **Sherlock**: Luego pruebo Sherlock, que busca nombres de usuario en redes sociales y plataformas. Tecleo "MarianoRajoy" y me salen un montón de resultados, pero como es famoso, muchos son memes o cuentas falsas. Para probar, busco mi propio nickname y veo que encuentra mis perfiles en GitHub y Twitter. "Esto sí que es útil para alguien menos conocido", reflexiono.

---

### **Paso 6: Comprobar si su correo ha sido filtrado**
Finalmente, quiero saber si ese correo inventado (o uno real que tuviera) ha sido comprometido en alguna filtración.

- **Have I Been Pwned**: Voy a Have I Been Pwned, ingreso el correo ficticio, y aunque no es real, imagino que si fuera suyo diría algo como: "Comprometido en filtraciones de Twitter y Daily Quiz". Esto significa que sus contraseñas podrían estar circulando por ahí.

- **IntelX**: Pruebo IntelX para buscar contraseñas filtradas. Con la versión gratuita no saco mucho, pero sé que la de pago podría darme más jugo. Lo dejo en mi lista de "herramientas a explorar".

- **Pentester.com**: Por último, analizo el correo en Pentester.com. Me da un informe ficticio con "14 problemas críticos", como datos expuestos en España y contraseñas filtradas. "Si esto fuera real, estaría en problemas", pienso.

---

### **Conclusión**
¡Y ahí lo tienes! Partiendo de una simple foto, descubrí que este señor es Mariano Rajoy, un político español. Averigüé dónde vive, dónde estudió, qué ha trabajado, conseguí un número y un correo (hipotéticos), y hasta revisé si sus datos han sido filtrados. Todo esto con herramientas públicas y un poco de curiosidad. Me encanta el OSINT porque demuestra cuánto se puede encontrar sin cruzar líneas éticas. Si te ha gustado, prueba estas herramientas tú mismo. ¡Nos vemos en la próxima aventura de investigación!