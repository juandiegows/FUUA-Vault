---
subject: Sistemas Operativos II
topic: Arquitectura de Hardware, Boot y Gestión de Usuarios
professor: Carlos Henry López Bermúdez
date: 2026-04-19
tags: [hardware, bios, uefi, assembly, boot-process]
---
---
# 📚 Detalle Técnico: Eje 1 - Sistemas Operativos II

## 📅 Pendientes y Checklist

- [ ] **Evaluación Eje 1 (20 pts):** Cierra mañana **20 de abril a las 23:59**. (10 preguntas, 30 min, 1 intento).
- [ ] **Evidencias Congreso (5 pts):** Redactar informe breve con capturas de pantalla del evento (15-17 abril).
- [ ] **Lectura Eje Referente 2:** Preparar conceptos de Kernel para la sesión del 22 de abril.
- [ ] **Verificación de Plataforma:** Asegurar que el examen se haya enviado correctamente y aparezca la nota cuantitativa.

---

## 🏗️ 1. Arquitectura del Chipset (Arquitectura Clásica)
El sistema operativo coordina los recursos mediante el chipset, que actúa como puente de comunicaciones.

### ⚡ Northbridge (Puente Norte)
Es el nodo de **alta velocidad**. Está conectado directamente al CPU a través del **FSB (Front Side Bus)**.
- **Responsabilidades:** - Gestión de la Memoria RAM.
	- Comunicación con la tarjeta de video (AGP / PCI Express).
- **Importancia:** Determina el tipo y velocidad de la memoria que el sistema puede usar.



### 🐢 Southbridge (Puente Sur)

Es el nodo de **baja velocidad**. Controla los periféricos de entrada/salida.
- **Responsabilidades:** - Controladores de disco (SATA/IDE).
	- Puertos USB, Audio y Red.
	- Reloj del sistema (CMOS) y soporte para la BIOS.
- **Flujo de datos:** Los periféricos envían datos al Southbridge, este al Northbridge y finalmente llegan al CPU.

---

## 🔄 2. El Proceso de Arranque (Bootstrapping)

El profesor detalló la secuencia lógica desde el encendido hasta la carga del Kernel.

1.  **Encendido y POST (Power On Self Test):** - Rutina en la ROM que verifica hardware (CPU, RAM, Chips de soporte).
    - Si falla: Códigos de pitidos (*Beeps*). Ejemplo: 2 pitidos = Error de paridad RAM.
2.  **Búsqueda del MBR (Master Boot Record):** - El firmware busca el primer sector del disco (512 bytes) que contiene la tabla de particiones y el código de inicio.
3.  **Carga del Boot Manager:** - Se accede al cargador (Windows Boot Manager o GRUB).
4.  **Transferencia al Kernel:** - El SO toma el control de los registros del procesador.



---

## 🛠️ 3. Capas de Abstracción: API, ABI y SCI

Como desarrollador (NestJS), estas capas definen cómo tu código interactúa con el silicio:

| Capa | Nombre Completo | Función Principal |
| :--- | :--- | :--- |
| **API** | Application Programming Interface | Funciones de alto nivel para el programador (Source Code). |
| **SCI** | System Call Interface | Puerta de entrada al Kernel para pedir recursos de hardware. |
| **ABI** | Application Binary Interface | Define la compatibilidad entre binarios y el SO (Machine Level). |

---

## ⌨️ 4. Lenguaje Ensamblador y Nemónicos

El **Ensamblador** es la representación humana del código máquina.
- **Nemónicos:** Códigos alfanuméricos que simbolizan tareas.
	- `MOV`: Mover datos entre registros.
	- `ADD`: Sumar valores.
	- `JMP`: Salto a otra línea de código.
- **Campos de una instrucción:**
	`Etiqueta | Operación (Nemónico) | Operandos | Comentario`



---

## 👥 5. Gestión de Cuentas y Perfiles

El SO administra la identidad para garantizar la **Confidencialidad, Integridad y Disponibilidad (C.I.D.)**.

### Tipos de Cuentas

- **Administrador:** Privilegios elevados, acceso al Modo Kernel.
- **Estándar:** Modo Usuario, no puede modificar archivos críticos del sistema.
- **Invitado:** Perfil temporal, sin persistencia de datos tras cerrar sesión.

### Tipos de Perfiles

- **Locales:** Guardados en el `C:\Users\` local.
- **De Red:** El perfil se descarga desde un servidor al iniciar sesión (Entornos corporativos).
- **Móviles/Nube:** Sincronización mediante cuentas de Microsoft/Google para mantener el entorno en múltiples dispositivos.

---
> [!warning] Tip para el examen
> El profesor mencionó que el **lenguaje ensamblador** es la representación más directa del código máquina específico para cada arquitectura. No olvides que **UEFI** permite programar aplicaciones antes de cargar el sistema operativo, algo que la BIOS no podía hacer.