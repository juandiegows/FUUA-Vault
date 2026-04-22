# 🔐 Criptografía III: Protocolos y Práctica

**Clase:** 09 de Abril, 2026

Link https://drive.google.com/file/d/1W5r2fyao5fcFmQQpCPWO2KYhdeELPYY5/view

---

### 🎯 Objetivos y Contexto Profesional

- **Enfoque 100% Práctico:** El curso se aleja de la teoría pura para centrarse en la implementación.
    
- **Déficit de Talento:** Existe un "hueco enorme" en el mercado laboral. La meta es que al finalizar, los estudiantes puedan orientarse a líneas de **Hacking Ético, Pentesting o Consultoría**.
    
- **Principio de Seguridad:** No se busca la invulnerabilidad (imposible), sino la **resiliencia**: que ante un ataque, los datos estén cifrados y el impacto sea nulo.
    

---

### 🗺️ El Escenario Global de Amenazas

A través de mapas como **Checkpoint** y **Kaspersky**, se analizaron los tipos de compromiso sobre los datos:

1. **Interrupción:** Ataques a la disponibilidad (DDoS).
    
2. **Interceptación:** Robo de información en tránsito (Sniffing).
    
3. **Modificación:** Alteración de la integridad de los datos.
    
4. **Fabricación:** Suplantación de identidad (Spoofing).
    

---

### 🛠️ Protocolos de Comunicación Segura (Análisis Técnico)

#### 1. IPSec (Internet Protocol Security)

Protege la comunicación a nivel de **capa de red** (Capa 3). Es esencial para túneles VPN.

- **Detalle Crítico:** Cifra la "carga útil" (payload) y puede autenticar las cabeceras IP para evitar que un atacante cambie el origen o destino.
    
- **Cifrado:** Utiliza algoritmos simétricos (como AES) por su velocidad en el manejo de grandes volúmenes de paquetes.
    

#### 2. SSL / TLS (The Gold Standard)

**TLS** es el sucesor de SSL y es el protocolo que vemos en acción con `HTTPS`.

- **Handshake (Apretón de manos):** Proceso donde cliente y servidor negocian versiones de cifrado y verifican certificados.
    
- **Híbrido:** Usa criptografía **asimétrica** para el intercambio de llaves y **simétrica** para la sesión de datos.
    
- **Diferencia Clave:** TLS puede proteger la Capa de Transporte y la de Internet simultáneamente.
    

#### 3. SSH (Secure Shell)

Reemplaza al inseguro _Telnet_. Proporciona un canal seguro sobre una red insegura.

- **Puerto por defecto:** `22`.
    
- **Seguridad:** Basada en pares de llaves (RSA/ED25519).
    

---

### 🧪 Preparación para el Laboratorio (Comandos y Setup)

Para la próxima clase (16 de abril), realizaremos el montaje de un servidor SSH. Aquí están los preparativos y comandos básicos que debes conocer:

#### 🖥️ Entorno de Virtualización

1. **VirtualBox:** Instalar la versión más reciente.
    
2. **Kali Linux:** Máquina atacante/herramienta.
    
3. **CSAP Security Station:** Máquina objetivo (Servidor).
    

#### ⌨️ Comandos Proactivos (Capa de Aplicación - SSH)

Si ya tienes tu máquina Linux, puedes ir practicando estos comandos de administración:

- **Instalar el servicio SSH (en Debian/Ubuntu/Kali):**
    
    Bash
    
    ```
    sudo apt update
    sudo apt install openssh-server
    ```
    
- **Verificar el estado del servicio:**
    
    Bash
    
    ```
    sudo systemctl status ssh
    ```
    
- **Generar un par de llaves (Criptografía Asimétrica):**
    
    Bash
    
    ```
    ssh-keygen -t rsa -b 4096
    ```
    
    _(Esto crea una llave privada `id_rsa` y una pública `id_rsa.pub` en `~/.ssh/`)_.
    
- **Conectarse a un servidor remoto:**
    
    Bash
    
    ```
    ssh usuario@direccion_ip_del_servidor
    ```
    

---

# 🌐 Mapas de Ciberataques en Tiempo Real

Para tu participación en la pregunta de los **5 puntos**, puedes explorar cualquiera de estos enlaces:

🛡️ **Checkpoint (ThreatCloud):** Es el que más se usó en clase para ver ataques a Bogotá y tipos de malware 
🔗 [https://threatmap.checkpoint.com/](https://threatmap.checkpoint.com/)

🌍 **Kaspersky (Cybermap):** El mapa 3D interactivo más popular 
🔗 [https://cybermap.kaspersky.com/es/](https://cybermap.kaspersky.com/es/)

🏹 **Fortinet (Threat Map):** Muy detallado en cuanto al origen y destino de los ataques 
🔗 [https://threatmap.fortiguard.com/](https://threatmap.fortiguard.com/)

🌊 **Digital Attack Map (Google/Arbor):** Especializado en ataques DDoS a nivel global 
🔗 [https://www.digitalattackmap.com/](https://www.digitalattackmap.com/)

☣️ **Bitdefender Live Map:** Muestra infecciones de malware y spam en tiempo real 
🔗 [https://threatmap.bitdefender.com/](https://threatmap.bitdefender.com/)

🤖 **Spamhaus (Botnet Analysis):** El mapa que mostró el profesor para ver la actividad de los bots 🔗 [https://www.spamhaus.com/threat-map](https://www.spamhaus.com/threat-map)

---

### 📝 Checklist de Pendientes y Evaluación

- [ ] **Actividad 1:** Informe de Laboratorio (Vence: **20 de abril**).
    
- [ ] **Pregunta de 5 Puntos:** Foro de participación sobre mapas de ciberataques.
    
- [ ] **Evaluación Docente:** Ya disponible en el portal (Realizar cuanto antes).
    
- [ ] **Setup Técnico:** Confirmar que **VirtualBox** abre las máquinas sin errores de arquitectura (VT-x/AMD-V).
    

---

#Criptografía #CyberSecurity #KaliLinux #SSH #TLS #Networking #Obsidian