
## 📅 **Horario GOD** (Optimiza tu día con enfoque y productividad)

| **Hora**              | **Actividad**                                      | **Misión SNS/SNP**                 | **Estado** |
| --------------------- | -------------------------------------------------- | ---------------------------------- | ---------- |
| **6:30 - 7:30 AM**    | Prepararte y alistarte                             | 🌿 _Ritual Matutino (SNP)_         | ✅ / ❌      |
| **7:30 - 7:50 AM**    | Concentración en el camino                         | ⚡ _Modo Alerta (SNS)_              | ✅ / ❌      |
| **7:50 - 8:00 AM**    | Llegada temprana al trabajo                        | 📅 _Planificación Relámpago (SNS)_ | ✅ / ❌      |
| **8:00 AM - 5:00 PM** | Trabajo (Usa tiempos libres para estudio)          | 🔥 _Modo Productividad (SNS)_      | ✅ / ❌      |
| **5:00 - 5:30 PM**    | Concentración en el camino de vuelta               | 🎯 _Reflexión Estratégica (SNP)_   | ✅ / ❌      |
| **5:30 - 5:50 PM**    | Ejercicio                                          | 💪 _Sprint de Adrenalina (SNS)_    | ✅ / ❌      |
| **5:50 - 6:10 PM**    | Baño y refrescarse                                 | 🌿 _Modo Zen (SNP)_                | ✅ / ❌      |
| **6:10 - 7:10 PM**    | Tareas y estudio                                   | 🔥 _Desafío Mental (SNS)_          | ✅ / ❌      |
| **7:10 - 8:10 PM**    | Curso de Ciberseguridad                            | 🛡️ _Subida de Nivel (SNS)_        | ✅ / ❌      |
| **8:10 - 8:40 PM**    | Cena                                               | 🍽 _Banquete Reparador (SNP)_      | ✅ / ❌      |
| **8:40 - 10:00 PM**   | Tiempo libre, relajación y preparación para dormir | 🌿 _Exploración Tranquila (SNP)_   | ✅ / ❌      |

---

## 7 misiones diarias: SNS (modo batalla) y SNP (modo zen) 

- **Lunes – Misión “Sprint de Adrenalina” (SNS):**  
    Inicia la semana con energía. Realiza una sesión de ejercicio intenso o enfócate en un desafío laboral que requiera decisiones rápidas para activar tu SNS. 
    ###### **(HIIT (High-Intensity Interval Training))**
    
- **Martes – Misión “Descanso Zen” (SNP):**  
    Dedica al menos 15 minutos a una meditación guiada o práctica de respiración profunda. Este día, elige actividades relajantes para fomentar la recuperación y reducir el estrés.
    
- **Miércoles – Misión “Combate contra el Dragón” (SNS):**  
    Enfrenta un reto inesperado o una situación estresante (puede ser en el trabajo o estudio) con enfoque y determinación, activando tu SNS para disparar tu alerta y concentración.
    ###### **Burpees**
    
- **Jueves – Misión “Oasis de Calma” (SNP):**  
    Programa una pausa prolongada: sal a caminar al aire libre, escucha música relajante o disfruta de un momento de lectura. El objetivo es activar tu SNP y restaurar la calma interna.
    
- **Viernes – Misión “Modo Superhéroe” (SNS):**  
    Acepta un desafío que requiera acción y liderazgo: presenta una idea, afronta una tarea complicada o realiza una actividad que te saque de tu zona de confort para activar tu SNS y sentirte imparable.
    ###### **Mountain Climbers**
    
- **Sábado – Misión “Tiempo de Reconexión” (SNP):**  
    Dedica tiempo a una actividad creativa o de ocio sin presiones (como pintar, escribir o disfrutar de un hobby), enfocándote en la relajación y conexión interior, activando tu SNP.
    
- **Domingo – Misión “Reflexión Estratégica” (SNP):**  
    Cierra la semana evaluando tus logros y aprendizajes. Dedica unos minutos a escribir tus reflexiones y planificar la semana siguiente de manera tranquila, permitiendo que tu SNP descanse y recargue energías.
    


## Tablero de Control Personal Integrado y Gamificado

### **Estructura del Tablero**

*En la columna **Horario GOD** marca:  
- **✓** si seguiste todos los bloques del horario (6:30 AM – 10:00 PM) sin interrupciones.  
- x si no cumpliste en absoluto.

[[historial_god]]

---
## Programa del Tablero de Control Personal:


````python

import csv

from datetime import datetime, timedelta

  

class GODSystem:

    def __init__(self):

        self.points = 0

        self.streak = 0

        self.level = 1

        self.daily_logs = []

        self.load_history()  # Cargar historial al iniciar

        self.calculate_initial_streak()  # Calcular racha inicial

  

    def load_history(self):

        """Carga los registros pasados desde 'historial_god.md'."""

        try:

            with open('historial_god.md', 'r', encoding='utf-8') as f:

                lines = f.readlines()

                if len(lines) < 1:

                    return  # No hay datos aún

                # Saltar la línea de separadores (primera línea si existe)

                start_index = 1 if lines[0].startswith('| -') else 0

                for line in lines[start_index:]:

                    if line.strip():

                        parts = [p.strip() for p in line.split('|')[1:-1]]

                        if len(parts) == 10:

                            try:

                                fecha = datetime.strptime(parts[0], "%d/%m/%Y")

                                self.daily_logs.append({

                                    "Fecha": fecha,

                                    "No Alcohol (0%)": parts[1],

                                    "No Media (0%)": parts[2],

                                    "No Porno (0%)": parts[3],

                                    "8H Descanso (100%)": parts[4],

                                    "Meditación (min)": int(parts[5]) if parts[5] else 0,

                                    "Buen Círculo (100%)": parts[6],

                                    "Ejercicio (5:30-5:50 PM)": parts[7],

                                    "Horario GOD": parts[8],

                                    "Certificaciones Avanzadas": parts[9]

                                })

                            except ValueError:

                                print(f"⚠️ Advertencia: La línea '{line.strip()}' no tiene una fecha válida y será ignorada.")

        except FileNotFoundError:

            pass  # Si el archivo no existe, comienza vacío

  

    def calculate_initial_streak(self):

        """Calcula la racha inicial basada en el historial."""

        if not self.daily_logs:

            self.streak = 0

            return

        sorted_logs = sorted(self.daily_logs, key=lambda x: x['Fecha'], reverse=True)

        current_streak = 0

        previous_date = None

        for log in sorted_logs:

            if log['Horario GOD'] != '✓':

                break

            if previous_date is None:

                current_streak += 1

                previous_date = log['Fecha']

            else:

                if log['Fecha'] == previous_date - timedelta(days=1):

                    current_streak += 1

                    previous_date = log['Fecha']

                else:

                    break

        self.streak = current_streak

  

    def calculate_daily_score(self, fecha_str, no_alcohol, no_media, no_porno, descanso_8h, minutos_meditacion, buen_circulo, ejercicio, horario_god, certificaciones):

        """Calcula puntos y actualiza la racha para un nuevo registro."""

        fecha = datetime.strptime(fecha_str, "%d/%m/%Y")

        daily_points = 0

  

        if self.daily_logs:

            latest_date = max(log['Fecha'] for log in self.daily_logs)

            consecutive = fecha == latest_date + timedelta(days=1)

        else:

            consecutive = True

  

        if horario_god == '✓':

            daily_points += 10

            if consecutive:

                self.streak += 1

            else:

                self.streak = 1

        else:

            self.streak = 0

  

        daily_points += 2 if no_alcohol == '✓' else 0

        daily_points += 2 if no_media == '✓' else 0

        daily_points += 2 if no_porno == '✓' else 0

        daily_points += 3 if descanso_8h == '✓' else 0

        daily_points += minutos_meditacion // 10

        daily_points += 2 if buen_circulo == '✓' else 0

        daily_points += 3 if ejercicio == '✓' else 0

  

        self.points += daily_points

        self.update_level()

  

        self.daily_logs.append({

            "Fecha": fecha,

            "No Alcohol (0%)": no_alcohol,

            "No Media (0%)": no_media,

            "No Porno (0%)": no_porno,

            "8H Descanso (100%)": descanso_8h,

            "Meditación (min)": minutos_meditacion,

            "Buen Círculo (100%)": buen_circulo,

            "Ejercicio (5:30-5:50 PM)": ejercicio,

            "Horario GOD": horario_god,

            "Certificaciones Avanzadas": certificaciones

        })

  

        self.save_to_file(fecha_str, no_alcohol, no_media, no_porno, descanso_8h, minutos_meditacion, buen_circulo, ejercicio, horario_god, certificaciones)

  

    def save_to_file(self, fecha, *args):

        """Guarda la entrada en 'historial_god.md' con formato Markdown limpio."""

        # Lista de valores para la fila

        columns = [fecha] + list(args)

        # Construir la fila sin espacios adicionales

        row = "| " + " | ".join(map(str, columns)) + " |\n"

        with open('historial_god.md', 'a', encoding='utf-8') as f:

            if f.tell() == 0:  # Archivo vacío, escribir encabezados y separadores

                headers = "| Fecha | No Alcohol (0%) | No Media (0%) | No Porno (0%) | 8H Descanso (100%) | Meditación (min) | Buen Círculo (100%) | Ejercicio (5:30-5:50 PM) | Horario GOD | Certificaciones Avanzadas |\n"

                separator = "| ---------- | :-------------: | :-----------: | :-----------: | :----------------: | :--------------: | :-----------------: | :----------------------: | :---------: | :-------------------------------------------------------------------: |\n"

                f.write(headers)

                f.write(separator)

            f.write(row)

  

    def update_level(self):

        """Actualiza el nivel basado en los puntos."""

        new_level = 1 + (self.points // 100)

        if new_level != self.level:

            self.level = new_level

            print(f"¡Subiste al nivel {self.level}!")

  

    def view_history(self):

        """Muestra el historial completo en la consola."""

        try:

            with open('historial_god.md', 'r', encoding='utf-8') as f:

                print(f.read())

        except FileNotFoundError:

            print("⚠️ No hay historial disponible.")

  

def get_valid_input(prompt, expected_type=str, allow_spaces=False):

    """Obtiene una entrada válida del usuario, sin espacios si allow_spaces es False."""

    while True:

        value = input(prompt).strip()

        if not allow_spaces and ' ' in value:

            print("⚠️ La respuesta no debe contener espacios. Intenta nuevamente.")

            continue

        if expected_type == int:

            try:

                return int(value)

            except ValueError:

                print("⚠️ Debes ingresar un número. Intenta nuevamente.")

        else:

            return value

  

def main():

    god_system = GODSystem()

  

    while True:

        print("\n--- Menú ---")

        print("1. Ingresar datos del día")

        print("2. Visualizar historial")

        print("3. Salir")

        option = input("Elige una opción (1-3): ").strip()

  

        if option == '1':

            fecha_str = get_valid_input("Ingresa la fecha (dd/mm/yyyy): ", allow_spaces=False)

            try:

                fecha = datetime.strptime(fecha_str, "%d/%m/%Y")

            except ValueError:

                print("⚠️ Formato de fecha incorrecto. Usa dd/mm/yyyy.")

                continue

  

            if any(log['Fecha'] == fecha for log in god_system.daily_logs):

                print("⚠️ Ya existe un registro para esta fecha.")

                continue

            print("\n¡Hola! Vamos a registrar tu progreso de hoy. Recuerda, cada pequeño paso cuenta. 🌟\n")

            print("\nRegistra tu progreso (usa ✓ o x, sin espacios):\n")

            no_alcohol = get_valid_input("¿Te abstuviste de alcohol? (✓/x): ", allow_spaces=False)

            no_media = get_valid_input("¿Evitaste redes sociales y contenido multimedia? (✓/x): ", allow_spaces=False)

            no_porno = get_valid_input("¿Te abstuviste de pornografía? (✓/x): ", allow_spaces=False)

            descanso_8h = get_valid_input("¿Dormiste 8 horas? (✓/x): ", allow_spaces=False)

            minutos_meditacion = get_valid_input("¿Cuántos minutos meditaste?: ", expected_type=int, allow_spaces=False)

            buen_circulo = get_valid_input("¿Te rodeaste de un buen círculo? (✓/x): ", allow_spaces=False)

            ejercicio = get_valid_input("¿Hiciste ejercicio? (✓/x): ", allow_spaces=False)

            horario_god = get_valid_input("¿Seguiste tu horario GOD? (✓/x): ", allow_spaces=False)

            certificaciones = get_valid_input("Avance en certificaciones (ej: Google:0% CompTIA:0% eJPTv2:25%): ", allow_spaces=True)

  

            god_system.calculate_daily_score(fecha_str, no_alcohol, no_media, no_porno, descanso_8h, minutos_meditacion, buen_circulo, ejercicio, horario_god, certificaciones)

  

            print(f"\nPuntos totales: {god_system.points}")

            print(f"Racha actual: {god_system.streak}")

            print(f"Nivel: {god_system.level}")

  

        elif option == '2':

            god_system.view_history()

  

        elif option == '3':

            print("¡Hasta luego!")

            break

  

        else:

            print("⚠️ Opción inválida. Elige 1, 2 o 3.")

  

if __name__ == "__main__":

    main()

`````

