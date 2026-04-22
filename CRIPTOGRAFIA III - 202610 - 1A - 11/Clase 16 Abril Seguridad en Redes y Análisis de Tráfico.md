
**Fecha:** 16 de Abril, 2026 **Herramientas:** VirtualBox 📦, Kali Linux 🐉, Wireshark 🦈.

https://drive.google.com/file/d/17W8KluqPj6buxPm5ahFu9Fsorc0p3E_l/view

## 🚀 Conceptos Iniciales de Linux

El profesor explicó que Linux maneja las interfaces y distros de forma distinta a Windows.

- **Interfaces comunes:** `eth0` (Ethernet), `enp0s3` o `lo` (Loopback/Localhost).
    
- **Lanzador de aplicaciones:** El equivalente al menú de inicio.
    

> [!TIP] **Comandos de Reconocimiento**
> 
> Bash
> 
> ```
> hostnamectl           # Ver info del sistema y la distro (Cali, Ubuntu, etc.)
> ifconfig              # Ver interfaces de red e IP actual
> clear                 # Limpiar la terminal
> ```

---

## 🕵️ Laboratorio 1: El peligro de Telnet (Inseguro)

**Objetivo:** Demostrar por qué no se deben usar protocolos sin cifrar.

### 📝 Paso a Paso:

1. Abrir **Wireshark** y seleccionar la interfaz de captura (ej. `any` o `loopback`).
    
2. En la terminal, ejecutar la conexión: `telnet localhost`.
    
3. Ingresar credenciales: usuario `Cisco` y password `password`.
    
4. Detener captura en Wireshark (botón rojo).
    
5. Aplicar filtro: `telnet`.
    
6. **Hallazgo:** Usar la lupa de búsqueda para encontrar cadenas de texto (login/password).
    

> [!WARNING] **Resultado** Los datos viajan en **texto plano**. Pudimos ver cada letra del password capturado en los paquetes.

---

## 🔐 Laboratorio 2: La robustez de SSH (Seguro)

**Objetivo:** Verificar que SSH cifra la comunicación.

### 📝 Paso a Paso:

1. Iniciar captura nueva en Wireshark.
    
2. Ejecutar conexión: `ssh Cali@<IP_DESTINO>`.
    
    - _Nota:_ Si el puerto 22 está bloqueado, usar `-p 443`.
        
3. Aplicar filtro en Wireshark: `ssh`.
    
4. **Hallazgo:** Al inspeccionar los paquetes, solo vemos "Encrypted Packet Data".
    

> [!SUCCESS] **Resultado** No hay forma de ver el contenido porque usa algoritmos de cifrado como **Chacha20** y curvas elípticas.

---

## 🛠️ Laboratorio 3: Configuración Avanzada de Servidor SSH

**Objetivo:** Asegurar un servidor y habilitar el acceso por llaves.

### 📝 Paso a Paso y Comandos:

1. **Editar configuración del puerto:**
    
    Bash
    
    ```
    sudo nano /etc/ssh/sshd_config
    # Cambiar "Port 22" a "Port 443"
    sudo service ssh restart   # Reiniciar el servicio para aplicar cambios
    ```
    
2. **Generar par de llaves (Pública/Privada):**
    
    Bash
    
    ```
    ssh-keygen   # Presionar Enter y asignar un passphrase si se desea
    ```
    
3. **Intercambio de llaves:**
    
    - Ver la llave generada: `cat ~/.ssh/id_rsa.pub`
        
    - Copiar ese código y pegarlo en el servidor dentro de: `nano ~/.ssh/authorized_keys`
        
4. **Entrar como Superusuario:**
    
    Bash
    
    ```
    sudo su     # Cambiar a usuario Root
    ```
    

---

## 🎁 Pregunta Sorpresa (Puntos Extra)

Para tu entrega, debes responder:

> **¿Por qué en el mundo Linux hablamos de "Distros" y "Releases" y no de "Versiones" como en Windows?**

---

## 📋 Checklist de Tareas para la Actividad

- [ ] Pantallazo de `hostnamectl` (identificar tu distro).
    
- [ ] Pantallazo de **Telnet** filtrado en Wireshark (donde se vea el password).
    
- [ ] Pantallazo de **SSH** (donde se vea el tráfico cifrado).
    
- [ ] Pantallazo de la generación de llaves con `ssh-keygen`.
    
- [ ] Responder la pregunta sorpresa de arriba.