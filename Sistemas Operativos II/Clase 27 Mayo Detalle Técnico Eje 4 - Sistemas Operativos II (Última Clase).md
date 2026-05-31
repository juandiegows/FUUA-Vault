---
fecha: 2026-05-27
asignatura: Sistemas Operativos II
eje: 4
tema: "Última Clase: iOS, Android, Sistemas Embebidos y Cierre de Semestre"
profesor: Carlos López
estado_entrega: Pendiente — Fecha límite lunes 2026-06-01 medianoche
estudio_adicional: Secure Boot iOS, Sandbox Android, Raspberry Pi vs Arduino, Obsolescencia Programada, OpenCore
---

# 📱 Guía de Ingeniería: iOS en Profundidad, Embebidos y Cierre de Semestre

## 1. Contexto Académico y Anuncios Finales

> [!WARNING] Fecha Límite de Entrega — Eje 4
> **Lunes 2026-06-01 a medianoche.** Sin excepciones. El profesor debe entregar notas el miércoles (~400 estudiantes). No hay prórroga: entrega tarde = **0.0**.

> [!IMPORTANT] Evaluación Docente
> Disponible en la página principal de la universidad. El profesor pidió que la realicen antes del cierre de semestre. Es anónima y le sirve para autoevaluar su metodología.

> [!SUCCESS] Última Sesión — Resumen de Cierre
> Esta fue la clase final del semestre. El profesor agradeció la participación activa del grupo, destacándolo como uno de los más participativos. Quedan pendientes solo la entrega del taller del eje 4.

---

## 2. Deep Dive: Arquitectura iOS — Cerrada y Segura

Continuando desde donde quedó la clase anterior (arquitectura cerrada de iOS):

### 2.1. ¿Qué significa "arquitectura cerrada por diseño"?
- El hardware y el sistema operativo se diseñan como un **ecosistema controlado por Apple**.
- Esto aumenta la compatibilidad interna y la seguridad, pero **impide la instalación en equipos no autorizados**.
- Por eso no es posible instalar iOS en un Samsung ni Android en un iPhone: cada uno viene diseñado de fábrica para soportar únicamente su software.

### 2.2. Componentes clave de seguridad en iOS

| Componente | Función |
| :--- | :--- |
| **CPU + GPU integrados** | Diseño Apple Silicon, optimizado para el SO propio |
| **Arranque seguro (Secure Boot)** | Verifica la cadena de integridad desde el chip hasta el SO en cada encendido |
| **Criptografía de hardware** | Cifrado de datos en reposo integrado al chip (no solo software) |
| **Actualizaciones OTA nocturnas** | iOS notifica, descarga y aplica parches automáticamente mientras el dispositivo carga — el usuario no ve el proceso técnico |

### 2.3. Flujo de Reinstalación de iOS

```
1. Instalar herramienta (iTunes / Finder / 3uTools)
        ↓
2. Conectar dispositivo vía cable USB de calidad
        ↓
3. Entrar en modo Recovery (Power + Home según modelo)
        ↓
4. Hacer respaldo (backup) ANTES de cualquier flash
        ↓
5. Descargar firmware compatible (versión correcta para el modelo)
        ↓
6. Ejecutar flash — NO desconectar hasta reinicio completo
        ↓
7. Restaurar desde backup → equipo listo
```

> **Truco de reinicio forzado:** Volumen arriba → Volumen abajo → mantener Power. Existe también un modo que arranca en **modo de instalación/recovery** y otro que borra todo. Conocer la diferencia evita pérdidas de datos.

---

## 3. Deep Dive: Android — Seguridad por Aislamiento y Permisos Explícitos

A diferencia de iOS, Android no es tan automático: requiere pasos más manuales y conscientes.

### 3.1. Mecanismos de seguridad de Android

| Mecanismo | Descripción |
| :--- | :--- |
| **UID/PID por app** | Cada aplicación y proceso tiene una identidad única del sistema. Separa usuarios, datos y ejecución. |
| **Sandbox (Caja de arena)** | Cada app opera aislada. No puede leer datos de otra app sin permiso explícito. |
| **Manifest de permisos** | La app declara al instalarse qué recursos necesita: cámara, ubicación, almacenamiento, micrófono, etc. |

### 3.2. Caso de análisis: App de linterna que pide contactos, ubicación y cámara
> Una linterna **no necesita** ubicación ni contactos. Si una app los pide, hay dos posibles causas:
> 1. **Recolección de datos para publicidad** (modelo freemium).
> 2. **Intención maliciosa** — spyware o adware encubierto.
>
> **Acción recomendada:** Denegar los permisos innecesarios o buscar una alternativa.

### 3.3. Pila de capas Android (recordatorio visual)

```
┌──────────────────────────────┐
│  Apps (Java / Kotlin)        │  No hablan directamente con el hardware
├──────────────────────────────┤
│  API / Framework             │  Media el acceso a sensores, cámara, red, audio
├──────────────────────────────┤
│  C / C++ Libraries           │  Librerías nativas del sistema
├──────────────────────────────┤
│  Hardware Abstraction Layer  │  Capa de abstracción de hardware (HAL)
├──────────────────────────────┤
│  Linux Kernel                │  Drivers, gestión de energía, memoria
└──────────────────────────────┘
```

> El usuario concede permisos que habilitan o bloquean el acceso de cada capa al hardware. Todo está en manos del usuario — si da permisos sin leer, asume el riesgo.

---

## 4. Instalación de Android: Checklist de Seguridad Antes de Flashear

> [!IMPORTANT] Verificar antes de hacer cualquier flash o reinstalación
> 1. **Versión compatible:** La ROM debe corresponder exactamente al modelo del dispositivo. Si llega una versión *inferior* a la instalada, sospechar y no instalar.
> 2. **Batería > 50%:** Regla normativa. iOS puede forzarse con menos si está conectado a corriente, pero Android generalmente bloquea el proceso.
> 3. **Cable USB de calidad:** Un cable defectuoso puede corromper la instalación a mitad del proceso.
> 4. **Drivers instalados en el PC:** El computador debe reconocer el móvil antes de iniciar.
> 5. **ROM descargada de fuente oficial:** Nunca de sitios de terceros no verificados.
> 6. **Herramienta correcta:** SP Flash Tool o Android Flash Tool según la plataforma.
> 7. **Plan B definido:** ¿Sabes hacer un hard reset si algo falla? ¿Tienes el backup hecho?

> [!WARNING] Cuidado crítico en SP Flash Tool
> Verificar siempre el **archivo scatter** y evitar cargar un preloader incorrecto. Un preloader equivocado puede **brickear el dispositivo** (dejarlo sin arranque).

---

## 5. Debate: Obsolescencia Programada y Marketing Tecnológico

La clase generó una discusión importante sobre por qué los fabricantes limitan las actualizaciones en equipos antiguos:

| Postura | Argumento |
| :--- | :--- |
| **Es marketing puro** | Los fabricantes diseñan los equipos con vida útil limitada para forzar la compra de nuevos modelos (retención de clientes). |
| **Es una limitación real de hardware** | Nuevas versiones de SO requieren más RAM, chips de IA, procesadores más rápidos. No es solo estrategia comercial. |
| **Existen alternativas** | Herramientas como **OpenCore** permiten instalar versiones no soportadas en Macs y PCs viejos. Windows 11 también tiene parches no oficiales para equipos "incompatibles". |
| **Riesgo de las alternativas** | Software no oficial puede tener código malicioso. El open source, aunque auditado por la comunidad, puede ser infiltrado por actores maliciosos. *(Aporte de Diego Borquez en el chat)* |

> **Reflexión del profesor:** *"Simplemente sabemos manejar los dispositivos pero no sabemos cómo tratarlos."* — Harrison comparte buenas prácticas: no cargar más del 80%, no bajar del 20%, usar siempre el cargador original.

> **Caso Samsung del profesor:** Compró un Galaxy (pantalla curva), lo cargó siempre con el cargador original. A los 366 días (garantía vencida hace 15 días), el teléfono nunca más prendió. Samsung negó garantía alegando "uso de cargador externo". Resultado: cambió a iOS y no volvió.

---

## 6. Deep Dive: Sistemas Embebidos — Raspberry Pi vs Arduino

### 6.1. Diferencia conceptual

| Característica | Raspberry Pi | Arduino |
| :--- | :--- | :--- |
| **Tipo** | Computadora miniaturizada | Microcontrolador dedicado |
| **SO** | Ejecuta Linux completo | No tiene SO — corre firmware |
| **Usos típicos** | Mini servidor, control de hogar inteligente, laboratorio de redes, procesamiento local | Sensores, actuadores, motores de paso, prototipos electrónicos, control simple y repetitivo |
| **Librerías** | Ecosistema Linux completo | FreeRTOS, librerías de Arduino IDE |
| **Instalación** | Imagen en microSD + Balena Etcher + arranque | Sketch cargado desde Arduino IDE por USB |

### 6.2. Instalación de Raspberry Pi OS

```
1. Descargar imagen del SO oficial (Raspberry Pi OS)
2. Escribir imagen en microSD con Balena Etcher
3. Conectar: microSD + cable red + teclado + mouse + alimentación
4. Arrancar y configurar
```

**Recursos mínimos:** microSD, cable de red, teclado, mouse, imagen del SO, herramienta para hacer booteable.

### 6.3. Instalación y programación de Arduino

```
1. Descargar Arduino IDE desde el sitio oficial (arduino.cc)
2. Conectar la placa por USB al PC
3. Verificar el puerto COM asignado
4. Escribir el sketch (setup + loop)
5. Compilar y cargar (flash) a la placa
```

> [!WARNING] Descarga solo desde arduino.cc oficial
> Si el IDE se descarga de un sitio no oficial, puede **quemar la placa**. Le pasó al profesor con estudiantes de semestres anteriores. El mismo IDE sirve para ESP32 con las librerías adicionales correspondientes.

### 6.4. Actualización de Firmware en dispositivos IoT

- Aplica a: routers, dispositivos IoT, embebidos en general.
- Es un cambio pequeño pero con gran impacto en seguridad y estabilidad.
- Más flexible que reinstalar un SO completo.
- Siempre descargar desde el fabricante oficial.

---

## 7. Políticas de Seguridad en Gestión de Dispositivos

> **Tríada de seguridad que no debe olvidarse:**
>
> - **Confidencialidad** — La información solo la ven quienes deben verla.
> - **Integridad** — La información no se altera sin autorización.
> - **Disponibilidad** — El sistema está accesible cuando se necesita.
>
> Estas tres propiedades deben integrarse al **plan de mantenimiento** de cualquier dispositivo móvil o embebido.

---

## 8. Actividad Eje 4 — Recordatorio Final

> [!IMPORTANT] Entrega: lunes 2026-06-01 a medianoche — sin excepciones

**Lo que debe subirse a Canvas:**
1. **Documento PDF** (Norma APA) con: portada, resumen + abstract en inglés, introducción, objetivos, descripción paso a paso, descripción de hardware/SO/apps, conclusiones, bibliografía.
2. **URL del video en YouTube** (3 a 6 minutos, audio explicativo propio).

**Sobre el video en grupo:**
- Lo sube **una sola persona** del grupo.
- Debe nombrar a **todos los integrantes con nombre y apellidos completos** (no solo nombres).
- Cada integrante sube su propio informe con el nombre completo del compañero incluido.

**Apps a seleccionar en Play Store (3 en total):**
- 1 para **cifrado/criptografía** de datos del dispositivo.
- 1 para **asegurar comunicaciones**.
- 1 para **localizar y borrar remotamente** en caso de pérdida o robo.

---

## 9. Materias que Dicta el Profesor (por si quieren buscarlo)

- Introducción a la Ingeniería
- Sistemas Operativos II
- Redes / Fundamentos de Redes
- Seguridad en Redes
- Administración y Gestión de Redes
- Informática Forense
- Formulación y Evaluación de Proyectos
- Gerencia de Proyectos
- Gestión y Evaluación de Proyectos
- También disponible como **director y jurado de trabajo de grado** (contactar al profesor Camilo).

---

## 10. Bibliografía de Consulta

- *Android Developers Documentation* — https://developer.android.com/security
- *Apple Platform Security Guide* — https://support.apple.com/guide/security/
- *Arduino Official IDE* — https://www.arduino.cc/en/software
- *Raspberry Pi Documentation* — https://www.raspberrypi.com/documentation/
- *Balena Etcher* — https://etcher.balena.io/
- *OWASP Mobile Top 10* — https://owasp.org/www-project-mobile-top-10/
- *NIST SP 800-124 Rev. 2* — Guidelines for Managing Mobile Device Security
