---
fecha: 2026-05-20
asignatura: Sistemas Operativos II
eje: 4
tema: Movilidad, Seguridad y Instalación de Sistemas Operativos Móviles y Embebidos
profesor: Carlos
estado_entrega: Pendiente
estudio_adicional: BYOD, Arquitecturas iOS vs Android, Firmware, Máquinas Virtuales, Norma APA
---

# 📱 Guía de Ingeniería: Movilidad, Seguridad y SO Móviles/Embebidos

## 1. Contexto Académico y Anuncios

> [!SUCCESS] Retroalimentación Eje 3
> El profesor terminó de calificar la mayoría de entregas. Si no estás de acuerdo con tu nota, escríbele por la **mensajería de Canvas** — revisará sin problema. Nunca bajará una nota por revisión, y reconoce que puede equivocarse.

> [!IMPORTANT] Evaluación Docente Abierta
> La evaluación docente ya está disponible. El profesor pidió que la realicen cuando se sientan cómodos. Los resultados le permiten autoevaluar su metodología. Es anónima.

> [!WARNING] Actividad de 5 Puntos — Eje 3
> La actividad de 5 puntos del eje 3 se activó con retraso (sábado en vez del viernes). El plazo se extendió hasta la **medianoche del 2026-05-20**. La del eje 4 se activará el viernes próximo y tendrá el plazo usual (viernes a lunes).

---

## 2. Pregunta Disparadora: ¿Quién responde por la seguridad de un dispositivo personal en red corporativa?

La clase abrió con este dilema y los estudiantes debatieron tres posiciones:

| Escenario | Responsabilidad |
| :--- | :--- |
| Dispositivo personal hackeado **dentro de la red corporativa** por vulnerabilidad de esa red | La empresa tiene responsabilidad parcial. Si hay evidencia forense del vector de ataque (puerto, servidor), la entidad responde. |
| Dispositivo personal hackeado desde red corporativa, pero el **dispositivo no es activo corporativo** | La empresa puede negarse: *"Ese equipo no nos corresponde."* El usuario queda desprotegido legalmente. |
| Cuenta corporativa/nómina hackeada desde **dispositivo y red corporativos** | La empresa responde completamente. |

> **Caso real citado en clase:** Un empleado perdió ~$20M COP por vulnerabilidad en la red de su empresa. Tanto la entidad bancaria como la empresa respondieron 50/50, mediado por la Superintendencia. La empresa respondió porque la red tenía credenciales asignadas a contratistas — era de uso corporativo, no pública.

**Conclusión del profesor:** La red corporativa es para activos corporativos. Conectar un dispositivo personal es riesgo del usuario. La empresa solo responde si el vector de ataque fue comprobadamente su infraestructura.

---

## 3. Deep Dive: BYOD y Vectores de Ataque Móvil

### 3.1. ¿Qué es BYOD?
**Bring Your Own Device** — política (o ausencia de política) que permite a los usuarios conectar sus dispositivos personales (teléfonos, tablets, portátiles) a redes corporativas.

| Ventaja | Riesgo |
| :--- | :--- |
| Mayor productividad y movilidad del empleado | Apps con permisos amplios fuera de control del área de TI |
| Ahorro en hardware para la empresa | Firmware desactualizado con vulnerabilidades conocidas |
| Flexibilidad de trabajo remoto | Punto de entrada a la red corporativa sin gestión MDM |

### 3.2. Riesgos Concretos Discutidos
- **Redes públicas gratuitas** (aeropuertos, parques con internet TIC, centros comerciales): Captura de información en menos de 30 segundos de conexión.
- **Permisos excesivos en apps:** El usuario hace clic sin leer y cede acceso a cámara, contactos, ubicación, almacenamiento.
- **SO desactualizados:** Un sistema sin parches es un vector abierto. Las actualizaciones cierran vulnerabilidades específicas, aunque no siempre lo digan explícitamente en el mensaje al usuario.
- **Phishing / links maliciosos:** Ingeniería social para ejecutar instalaciones silenciosas de malware o spyware.

> **Dato interesante del profesor:** En aeropuertos internacionales (ej. Frankfurt, El Dorado), conectarse a la red Wi-Fi gratuita entrega tus datos al sistema. En Colombia, la Fiscalía tiene equipos conectados directamente a las operadoras móviles para investigación. El Dorado es uno de los aeropuertos con mayor vigilancia de este tipo en Latinoamérica.

> **Caso pandemia (Harrison):** Durante la pandemia, redes Wi-Fi públicas desplegadas por la Consejería Distrital de TIC recopilaban datos de conexión (nombre, documento) para construir bases de datos de migrantes, personas con discapacidad y otros indicadores para la Alcaldía de Bogotá.

### 3.3. Respuesta desde TI
Para mitigar el riesgo BYOD, el departamento de TI debe implementar:
- **Políticas de acceso:** Qué dispositivos pueden conectarse y con qué credenciales.
- **Actualización y respaldo:** Control de versiones de SO y backups.
- **Control de acceso (IAM/MDM):** Gestión de identidades y dispositivos móviles.
- **Orientación al usuario:** Capacitación sobre riesgos y buenas prácticas.

> **Idea clave del profesor:** *"Gestionar dispositivos no es solo instalar software, es equilibrar seguridad, privacidad y servicio."*

---

## 4. Deep Dive: Ecosistema Móvil vs. Sistemas Embebidos

### 4.1. Capas de Arquitectura Móvil (Android/iOS)

```
┌─────────────────────────────────┐
│         APLICACIONES            │  Inicio, cámara, navegador, apps de terceros
├─────────────────────────────────┤
│       FRAMEWORK / API           │  Vistas, recursos, notificaciones, permisos
├─────────────────────────────────┤
│          RUNTIME                │  Librerías compartidas, servicios del SO
├─────────────────────────────────┤
│     KERNEL / CORE DEL SO        │  Drivers, seguridad, red, almacenamiento
├─────────────────────────────────┤
│           HARDWARE              │  CPU, GPU, cámara, radios, sensores
└─────────────────────────────────┘
```

### 4.2. iOS vs. Android: Diferencias Arquitectónicas

| Característica | iOS | Android |
| :--- | :--- | :--- |
| **Modelo** | Cerrado (ecosistema Apple) | Abierto (múltiples fabricantes) |
| **Integración HW/SW** | Alta — Apple controla ambas capas | Variable — depende del fabricante |
| **Kernel base** | Darwin (BSD/XNU) | Linux |
| **Arranque** | Secure Boot fuerte, controlado por Apple | Varía por fabricante; permite desbloques |
| **Permisos** | Control estricto por app desde iOS 14+ | Sandbox por aplicación, más configurable |
| **Actualizaciones** | Centralizadas, Apple las envía directamente | Fragmentadas: Android base → fabricante → operadora |
| **Usuarios** | Minoría (ecosistema premium) | Mayoría global |

> **¿Por qué no puedo instalar iOS en un Samsung?** Porque la arquitectura del hardware ya viene diseñada de fábrica para soportar un software específico. La compatibilidad depende de: **Dispositivo + Firmware + Herramienta + Procedimiento exacto**.

### 4.3. Sistemas Embebidos vs. Móviles

| Aspecto | Dispositivos Móviles | Sistemas Embebidos |
| :--- | :--- | :--- |
| **Ejemplos** | Smartphones, tablets | Raspberry Pi, Arduino, routers, IoT |
| **Reinstalación** | Factory reset / ROM flash | Arranque desde medio externo, flash de firmware |
| **Proceso de actualización** | OTA (Over The Air) | Requiere herramienta externa, más técnico |
| **Flexibilidad** | Alta (app stores, permisos de usuario) | Baja (propósito específico) |
| **Stack mínimo** | Hardware + Drivers/Kernel + Servicios + Apps | Hardware + Drivers/Kernel + Firmware |

---

## 5. Tarea Sorpresa / Actividad de 5 Puntos

> [!WARNING] Pregunta que "dejó caer" el profesor
> *"Para instalar o actualizar hay que respetar la combinación exacta. ¿Cuál es?"*
> **Respuesta:** `Dispositivo + Firmware + Herramienta + Procedimiento`
> El profesor dijo textualmente: *"Yo creo que esta pregunta la voy a dejar de los cinco puntos. Ahí se me chispoteó."* — Memorízala.

---

## 6. Actividad del Eje 4 (Taller Grupal — Última entrega)

> [!IMPORTANT] Descripción Completa de la Actividad
> **Modalidad:** Grupal (interacción grupal vale puntos en la rúbrica — si lo entregas solo, saca 0 en ese ítem).
> **Tema:** Instalación de Android en máquina virtual.

### Pasos a seguir:
1. Leer el referente del eje 4 y ver todas las videocápsulas.
2. Verificar los **requisitos de hardware** para instalar Android (referente).
3. Instalar un software de virtualización: **VirtualBox** o **VMware**.
4. Descargar una **ROM de Android** desde los recursos del referente.
5. Instalar Android sobre la máquina virtual siguiendo el video del link anexo.
6. Reiniciar la VM y **personalizar la distribución** de Android instalada.
7. Entrar a **Play Store** y seleccionar **3 apps** de seguridad:
   - Una para **cifrado/criptografía** de datos.
   - Una para **asegurar comunicaciones**.
   - Una para **localizar y borrar remotamente** en caso de robo/pérdida.

### Documento a entregar (Norma APA):
- Portada
- **Resumen en español** + **Abstract en inglés** (párrafo o dos, va antes de la introducción)
- Palabras clave / Keywords
- Introducción
- Objetivos
- Descripción detallada de cada paso con capturas
- Descripción de: plataforma de hardware, SO instalado, apps seleccionadas
- Conclusiones
- Referencias bibliográficas

> [!WARNING] Dato clave del abstract
> Si el profesor ve el resumen en español + abstract en inglés en tu informe, asume que **estuviste en clase o viste la grabación**. Es la señal diferenciadora.

### Video a entregar:
- Duración: **3 a 6 minutos** (máximo).
- Debe incluir audio explicativo (tú mismo narrando).
- Contenido: explicación de la ROM elegida, características de la VM, versión de Android, descripción breve de las 3 apps.
- Publicar en **YouTube** (u otra plataforma de streaming gratuita).
- Subir a Canvas: el **documento PDF** + el **enlace al video**.

### Rúbrica (ítems clave):
| Ítem | Qué evalúa |
| :--- | :--- |
| Uso de herramientas | Correcta instalación y uso de la VM y Android |
| Pensamiento crítico | Justificación de decisiones técnicas |
| Interacción grupal | Evidencia de trabajo en equipo — **0 si es individual** |

---

## 7. Ruta de Aprendizaje — Próxima Sesión (última clase)

La próxima sesión continuará con:
- Instalación de iOS (conceptual, sin práctica — no todos tienen hardware Apple)
- Arquitectura de seguridad iOS en profundidad
- Sistemas embebidos: Raspberry Pi, Arduino, firmware

> El profesor pidió que para esa sesión ya hayan revisado los videos y avanzado en la actividad.

---

## 8. Bibliografía de Consulta

- *Documentación oficial de Android Developers* — https://developer.android.com
- *VirtualBox User Manual* — https://www.virtualbox.org/manual/
- *OWASP Mobile Security Testing Guide* — https://owasp.org/www-project-mobile-security-testing-guide/
- *Tanenbaum, A. S.* — Modern Operating Systems (cap. sobre SO móviles)
- *NIST SP 800-124* — Guidelines for Managing the Security of Mobile Devices in the Enterprise
