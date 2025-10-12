

### **Resumen de la Actividad: Investigación de Analizadores de Protocolos de Red**

En esta actividad, tu rol como analista de ciberseguridad es investigar y comparar dos herramientas fundamentales de análisis de red: **Wireshark** y **tcpdump**. El objetivo es comprender sus características, funcionalidades, diferencias y similitudes para determinar sus casos de uso ideales.

#### **Escenario**

Se te ha encargado investigar las diferencias y similitudes entre Wireshark y tcpdump. Debes crear un gráfico o una tabla que resuma tus hallazgos, destacando al menos dos diferencias y tres similitudes clave.

#### **Instrucciones Clave**

1. **Investigación:** Utiliza recursos fiables como la documentación oficial, sitios de ciberseguridad de buena reputación y foros técnicos para recopilar información sobre ambas herramientas.
    
2. **Puntos a Considerar:**
    
    - **Acceso y Licencia:** ¿Cómo se accede a la herramienta? ¿Es de código abierto o propietaria?
        
    - **Interfaz de Usuario (UI):** ¿Qué tipo de interfaz utiliza (gráfica o línea de comandos)?
        
    - **Casos de Uso:** ¿Cómo y cuándo la utilizan los analistas de seguridad?
        
    - **Funcionalidades:** ¿Cómo gestionan la captura, el análisis y el filtrado de tráfico?
        
    - **Limitaciones:** ¿Existen consideraciones o desventajas al usar cada herramienta?
        
3. **Resultado Final:** Rellena una plantilla de diagrama con tus hallazgos, incluyendo:
    
    - Al menos **2 diferencias** entre Wireshark y tcpdump.
        
    - Al menos **3 similitudes** entre ellas.
        

---

### **Análisis Comparativo: Wireshark vs. tcpdump**

A continuación se presenta el análisis comparativo solicitado, estructurado para ser utilizado en tu diagrama.

#### **Diferencias**

|Característica|Wireshark|tcpdump|
|---|---|---|
|**Interfaz de Usuario**|**Interfaz Gráfica de Usuario (GUI):** Ofrece una experiencia visual e interactiva que facilita el análisis profundo, el coloreado de paquetes y la navegación.|**Interfaz de Línea de Comandos (CLI):** Funciona a través de texto en la terminal, lo que la hace ligera, rápida y ideal para automatización y acceso remoto.|
|**Uso de Recursos y Escenario Ideal**|**Análisis profundo y post-captura:** Consume más CPU y memoria. Es ideal para un análisis forense detallado en una estación de trabajo dedicada.|**Captura en vivo y monitoreo continuo:** Consume muy pocos recursos. Es perfecta para capturar tráfico durante largos períodos en servidores, routers o sistemas con capacidad limitada.|

#### **Similitudes**

- **Propósito Fundamental:** Ambas son **analizadores de protocolos de red** (_packet sniffers_). Su función principal es capturar, mostrar y permitir la inspección del tráfico de datos que atraviesa una interfaz de red.
    
- **Código Abierto (Open Source):** Tanto Wireshark como tcpdump son proyectos de software libre y de código abierto. Esto significa que son gratuitos, transparentes y mantenidos por una comunidad global de desarrolladores.
    
- **Compatibilidad de Formato:** Ambas herramientas utilizan la librería subyacente **`libpcap`** para la captura de paquetes. Como resultado, son totalmente compatibles con el formato de archivo estándar **`.pcap`**, permitiendo que los datos capturados con una herramienta sean analizados con la otra.
