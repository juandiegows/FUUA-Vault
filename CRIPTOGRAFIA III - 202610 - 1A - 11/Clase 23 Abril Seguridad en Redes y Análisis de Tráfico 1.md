
## 🎓 Resumen de Clase: Seguridad en Correo Electrónico

### 📝 Tarea de los 5 Puntos (Tarea Sorpresa)

El objetivo es completar la tabla de compromisos y técnicas de ataque mencionada en clase. Debes investigar y ubicar los siguientes conceptos según el **atributo afectado** (Privacidad, Integridad, Identidad, Disponibilidad) y el **compromiso** generado:

- **Términos a ubicar:**
    
    1. Malware adjunto.
        
    2. Ataques de Spam.
        
    3. Mail Bombing.
        
    4. Ataques a listas de distribución.
        
    5. Credential Harvesting.
        
    6. Fugas de información.
        

> [!TIP]
> 
> Puedes apoyarte en el slide de la clase (minuto 34:00) para ver la estructura de la tabla.

---

### 🚀 Preparación para el Laboratorio (Paso a Paso)

Para la próxima clase (dentro de 8 días), debemos tener listo el entorno de trabajo para el intercambio seguro de correos en parejas.

#### 1. Instalación de Herramientas PGP

- **Paso 1:** Descargar e instalar **Gpg4win**.
    
    - Ir a la sección de Software > [Gpg4win](https://gpg4win.org/).
        
- **Paso 2:** Instalar la extensión **Mailvelope** en el navegador (Chrome preferiblemente).
    
    - Esta permite cifrar correos directamente desde el webmail.
        
- **Paso 3:** Descargar el cliente de correo **Thunderbird**.
    
    - Se usará para configurar los protocolos de forma local.
        

#### 2. Configuración de Parejas

- La actividad es estrictamente en **parejas** (grupos de 2).
    
- El objetivo es generar un par de llaves (pública/privada) e intercambiar correos cifrados y firmados.
    

---

### 💻 Conceptos y Protocolos Técnicos

A continuación, los comandos lógicos y protocolos discutidos para entender el flujo del correo:

|**Protocolo**|**Función Principal**|**Puerto Estándar**|**Puerto Seguro (Cripto)**|
|---|---|---|---|
|**SMTP**|Transferencia de correo (Salida)|25|587|
|**POP3**|Descarga correos del servidor (Libera espacio)|110|995|
|**IMAP**|Acceso a mensajes (Mantiene copia en servidor)|143|993|
|**MIME**|Formato de contenido enriquecido (Adjuntos, tildes)|N/A|N/A|

#### 🛡️ Diferencias Clave: PGP vs S/MIME

- **Open PGP:**
    
    - **Comando/Uso:** Basado en un modelo de "Red de Confianza".
        
    - **Licencia:** Open Source (Gratuito).
        
    - **Servicios:** Confidencialidad, Integridad, Autenticación y Compresión.
        
- **S/MIME:**
    
    - **Comando/Uso:** Basado en Jerarquía de Certificados (X.509) y PKI.
        
    - **Licencia:** Licenciado (De pago, común en entornos corporativos como Outlook/Exchange).
        
    - **Servicios:** Agrega el **No Repudio** (trazabilidad legal).
        

---

### 🛠️ Flujo Lógico de Cifrado PGP (Comandos Internos)

1. **Generación:** Se crea una **llave aleatoria de sesión** (Cifrado Simétrico) para cifrar el cuerpo del mensaje.
    
2. **Protección:** Esa llave de sesión se cifra con la **Llave Pública** del receptor (Cifrado Asimétrico RSA/ElGamal).
    
3. **Envío:** Se manda el paquete (Mensaje Cifrado + Llave de Sesión Cifrada).
    
4. **Recepción:** El receptor usa su **Llave Privada** para extraer la llave de sesión y luego descifrar el mensaje.
    

---

### 📌 Notas Finales para Obsidian

- **Fecha de entrega:** Próxima clase.
    
- **Entregable:** Informe en PDF (individual, aunque el trabajo sea en pareja).
    
- **Emojis clave:**
    
    - 📧 Correo
        
    - 🔒 Cifrado
        
    - 🔑 Llaves
        
    - ⚠️ Riesgo/Ataque
        

---

_Resumen generado para el seguimiento del eje 2 - Criptografía._