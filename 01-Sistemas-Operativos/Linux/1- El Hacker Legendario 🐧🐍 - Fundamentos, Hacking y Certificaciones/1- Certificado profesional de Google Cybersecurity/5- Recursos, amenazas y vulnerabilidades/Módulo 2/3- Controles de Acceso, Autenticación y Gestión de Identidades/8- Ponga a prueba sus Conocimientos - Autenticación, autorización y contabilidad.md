---
tipo: teoria
tags: [google-cybersecurity, el-hacker-legendario, modulo-2]
actualizado: 2026-05-28
---

# Ponga a prueba sus Conocimientos - Autenticación, autorización y contabilidad

### **Pregunta 1**

**¿Qué factores utilizan los sistemas de autenticación para verificar la identidad de un usuario? (3 respuestas)**

- **Conocimientos** → Algo que el usuario _sabe_, como una contraseña, PIN o respuesta secreta.
    
- **Posesión** (_en la traducción salió como “Responsabilidad”_) → Algo que el usuario _tiene_, como una tarjeta inteligente, un token de seguridad, o el celular con una app de autenticación.
    
- **Características** → Algo que el usuario _es_, es decir, biometría como huella dactilar, iris, reconocimiento facial o voz.
    

👉 Estos son los **tres factores clásicos de autenticación**: _algo que sabes, algo que tienes y algo que eres_.

---

### **Pregunta 2**

**¿Cómo se benefician las empresas al implementar inicio de sesión único (SSO)? (2 respuestas)**

- **Proporcionando una mejor experiencia del usuario** → El usuario solo necesita un inicio de sesión para acceder a múltiples aplicaciones, evitando recordar muchas contraseñas.
    
- **Simplificando la gestión de usuarios** → Los administradores gestionan centralmente las cuentas y accesos, lo que reduce errores y facilita dar o revocar permisos.
    

👉 El beneficio real de SSO no es más seguridad por sí mismo, sino **eficiencia**: menos contraseñas que manejar, menor carga administrativa, y usuarios más productivos.

---

### **Pregunta 3**

**Una empresa minorista divide funciones entre tres empleados: comprar, aprobar y pagar facturas. ¿Qué principio aplica?**

- **Separación de funciones** → Evita que una sola persona tenga control total de un proceso crítico.  
    Ejemplo: Si una persona pudiera comprar, aprobar y pagar, tendría oportunidad de cometer fraude sin supervisión.
    

👉 Es una práctica de **control interno y seguridad**, muy usada en contabilidad, bancos y sistemas críticos.

---

### **Pregunta 4**

**¿Cuáles son las categorías de controles de acceso? (3 respuestas)**

- **Autenticación** → Verifica la identidad (¿quién eres?).
    
- **Autorización** → Determina lo que puedes hacer (¿qué permisos tienes?).
    
- **Contabilidad (Accounting)** → Registra y audita las acciones del usuario (¿qué hiciste y cuándo?).
    

👉 Estas tres forman el famoso modelo **AAA (Authentication, Authorization, Accounting)**. Sin el tercer paso (contabilidad), no habría trazabilidad ni responsabilidad.

---

### **Pregunta 5**

**¿Qué credencial utiliza OAuth para autenticar a los usuarios?**

- **Token de API** → Es un código digital que se entrega a una aplicación o servicio y que valida que el usuario ya fue autenticado.  
    Ejemplo: cuando entras a una app con tu cuenta de Google, OAuth no comparte tu contraseña, sino un _token_ temporal que confirma tu identidad.
    

👉 Esto da seguridad porque **no se exponen credenciales reales**, y los permisos se pueden limitar o revocar fácilmente.

---

---

## Navegación

- ⬆️ Carpeta: [[_5- Recursos, amenazas y vulnerabilidades|5- Recursos, amenazas y vulnerabilidades]]
- ⬅️ Anterior: [[7- Actividad - Mejorar la autenticación, autorización y contabilidad de una pequeña empresa (Business to Business)]]
