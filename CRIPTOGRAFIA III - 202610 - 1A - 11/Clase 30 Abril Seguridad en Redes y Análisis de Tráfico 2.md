## 🛡️ Resumen de Clase: Criptografía Práctica (PGP & S/MIME)

### 📝 Tarea de los 5 Puntos (Tarea Sorpresa)

Para asegurar los puntos de la actividad, debes entregar un documento con:

1. **Capturas de pantalla** de cada proceso (Generación, Importación, Cifrado y Descifrado).
    
2. **Investigación de costos**: Consultar el precio de un certificado **S/MIME** en proveedores como GlobalSign, DigiCert o similares.
    
3. **Análisis de S/MIME**: Responder por qué el administrador del servidor (ej. el de la universidad) debe habilitar la opción y por qué no puedes hacerlo tú como usuario final.
    

---

### 🚀 Paso a Paso de la Práctica

#### Fase 1: Preparación de Entorno

- **Software utilizado:** GPG4Win (que incluye el gestor de llaves **Kleopatra**).
    
- **Extensión de navegador:** Mailvelope (para cifrado directo en Webmail).
    

#### Fase 2: Gestión de Llaves en Kleopatra

1. **Generar par de claves:**
    
    - Ir a `Archivo` -> `Nuevo par de claves PGP`.
        
    - Ingresar nombre y correo electrónico real (institucional).
        
    - **Opciones avanzadas:** Se recomienda usar **RSA 4096** (más seguro) o **Curve 448** (más eficiente).
        
    - Establecer fecha de vencimiento (ej. 1 año).
        
    - Crear una **frase de contraseña** (capa extra de seguridad).
        
2. **Exportar Llave Pública:**
    
    - Clic derecho sobre tu certificado -> `Exportar`.
        
    - Guardar como archivo `.asc` (este es el que se comparte).
        

#### Fase 3: Intercambio y Servidores Globales

1. **Subir a Servidor Público:**
    
    - Ingresar a [keys.openpgp.org](https://keys.openpgp.org/).
        
    - Subir el archivo `.asc`.
        
    - **Paso Crítico:** Revisar el correo y hacer clic en el link de validación para que la llave sea buscable.
        
2. **Importar llaves de compañeros:**
    
    - Buscar por correo en el servidor o recibir el archivo `.asc`.
        
    - En Kleopatra: `Importar` -> Seleccionar archivo.
        
    - **Certificar llave:** Clic derecho sobre la llave del compañero -> `Certificar`. Esto crea una relación de confianza.
        

#### Fase 4: Cifrado de Archivos y Correos

1. **Cifrar archivos locales:**
    
    - Botón `Firmar / Cifrar` en Kleopatra.
        
    - Seleccionar destinatario (usa su llave pública).
        
    - Se genera un archivo `.pgp`.
        
2. **Uso de Mailvelope (Cifrado en el navegador):**
    
    - Importar las llaves en el candado de Mailvelope.
        
    - En Gmail/Outlook, usar el botón de redactar seguro (icono de papel con candado).
        
    - Escribir mensaje y dar clic en `Cifrar`.
        

---

### 💻 Comandos y Conceptos Clave

|**Acción**|**Herramienta / Ruta**|**Nota Técnica**|
|---|---|---|
|**Cifrar**|Llave Pública del destinatario|Solo el dueño de la privada puede abrirlo.|
|**Firmar**|Llave Privada del emisor|Garantiza autenticidad y no repudio.|
|**Descifrar**|Llave Privada propia|Requiere la frase de contraseña.|
|**Algoritmo Sugerido**|RSA 4096|El estándar de oro en seguridad asimétrica.|

---

### ⚠️ Verificación de S/MIME

Durante la clase se verificó en **Office 365** y **Hotmail**:

- **Resultado:** No está habilitado por el administrador de la organización.
    
- **Ruta de verificación:** `Configuración` -> `Correo` -> `S/MIME`.
    
- **Conclusión:** A diferencia de PGP (que es descentralizado y gratuito), S/MIME requiere una infraestructura de clave pública (PKI) gestionada por la empresa y certificados pagos.