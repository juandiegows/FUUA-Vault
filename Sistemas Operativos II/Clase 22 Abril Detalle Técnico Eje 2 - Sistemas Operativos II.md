---
fecha: 2026-04-24
asignatura: Sistemas Operativos
eje: 2
tema: Arquitectura y Seguridad en Sistemas Operativos
profesor: Raúl Bareño
estado_entrega: Pendiente
estudio_adicional: Arquitectura Harvard, Niveles de Privilegio (Rings), Escalabilidad Cloud
---

# 🖥️ Guía de Ingeniería: Arquitectura y Seguridad de Sistemas

## 1. Contexto Académico y Puntos Extra

> [!SUCCESS] Tarea de 5 Puntos: Congreso de IA
> **Actividad:** Validación de asistencia al congreso "Aprendizaje en la era de la IA".
> **Requisitos:** > 1. Pantallazo con nombre visible en la plataforma.
> 2. Responder: *¿Cómo se llama el conferencista?* (Dra. Paola Marambio).
> **Nota:** El profesor realizó la retroalimentación hoy; la actividad está cerrada, pero se resaltó la frase: *"El futuro es humano CON máquina"*.

---

## 2. Deep Dive: Arquitecturas de Hardware y Procesamiento
El profesor discutió cómo el diseño físico influye en el rendimiento del SO. Aquí expandimos la base técnica:

### 2.1. Evolución de la CPU: Von Neumann vs. Harvard
* **Arquitectura Von Neumann:** Basada en un único bus para datos e instrucciones. 
    * *Limitación:* El "Cuello de botella de Von Neumann", donde la CPU no puede acceder a ambos al mismo tiempo, limitando la velocidad de procesamiento.
* **Arquitectura Harvard:** Utilizada en sistemas de alto rendimiento y microcontroladores modernos. Posee memorias físicas y buses separados para instrucciones y datos.
    * *Ventaja Técnica:* Permite el **Pipelining** (segmentación), donde la CPU lee la siguiente instrucción mientras ejecuta la actual, optimizando ciclos de reloj.



### 2.2. Modos de Ejecución y Protección (Rings)
Para evitar que un software mal programado destruya el hardware, los sistemas modernos implementan anillos de protección:
* **Modo Usuario (Ring 3):** Las aplicaciones corren aquí. Tienen prohibido el acceso directo a la memoria física o al hardware. Si intentan una operación prohibida, el procesador genera una **Excepción de Protección General** y el SO termina el proceso (Aislamiento de fallos).
* **Modo Kernel (Ring 0):** Es el nivel de máximo privilegio donde reside el núcleo del SO.
    * *Peligro:* Un fallo en este modo corrompe las estructuras de datos globales, resultando en un **Kernel Panic** (Linux) o **BSOD** (Windows). Requiere reinicio físico del hardware.



---

## 3. Escalabilidad y Redes Corporativas
El diseño modular es lo que permite que un sistema crezca según la demanda de los usuarios.

### 3.1. Tipos de Escalabilidad
| Tipo | Descripción Técnica | Caso de Uso |
| :--- | :--- | :--- |
| **Vertical (Scaling Up)** | Añadir más recursos (RAM, CPU, NVMe) a un único nodo/servidor. | Bases de datos monolíticas que requieren baja latencia. |
| **Horizontal (Scaling Out)** | Añadir más nodos o instancias a un clúster o detrás de un Load Balancer. | Aplicaciones web y servicios en la nube (AWS EC2 Autoscaling). |

### 3.2. Arquitectura de Red: P2P vs. Cliente-Servidor
* **Redes P2P:** Bajo costo, pero alta vulnerabilidad. No hay control centralizado de identidades.
* **Cliente-Servidor:** Basado en protocolos asimétricos. El servidor aguarda pasivamente (standby) hasta recibir peticiones. Es la base de la seguridad centralizada y la integridad de datos.

---

## 4. Proyecto: Caso 'Protejo sus datos' (Sprint Backlog)

> [!IMPORTANT] Análisis del Requerimiento
> La empresa busca seguridad 24/7. La propuesta de los socios de usar un Switch doméstico y computadores administrativos para gestionar AWS es un **Riesgo Crítico de Seguridad** y una falla de arquitectura.

### Tareas de Ingeniería:
- [ ] **Wiki Colaborativa:** Justificar técnicamente por qué la infraestructura doméstica no garantiza disponibilidad 24/7.
- [ ] **Diseño de Seguridad:** Proponer el uso de **Bóvedas de Archivos** y gestión de privilegios (IAM en AWS).
- [ ] **Estrategia de Backup:** Implementar la lógica de "transparencia de ubicación" y backups externos (lección de las Torres Gemelas/Disaster Recovery).
- [ ] **Estructura del Informe:** Entregar PDF con Normas APA y todos los ítems de la universidad.

---

## 5. Consideraciones Críticas y Reglas de Oro

> [!WARNING] Advertencias del Profesor (Raúl Bareño)
> 1. **Permisos de URL:** Si realizas el **Reto Extra** (Wiki como Web App/Google Sites), debes dar permisos explícitos a `celoz167@areandina.edu.co`. **Link privado = Nota 0.0**.
> 2. **Creatividad:** El reto de la página web es opcional pero suma puntos significativos. Se valoran diseños dinámicos (clics, transiciones, interactividad).
> 3. **Puntualidad:** Fecha límite **04 de mayo**. No habrá prórrogas.
> 4. **Cámara:** En la próxima sesión, el profesor restará puntos a quienes no tengan la cámara encendida.

### Bibliografía de Consulta
* *Tanenbaum, A. S.* - Modern Operating Systems.
* *AWS Documentation* - Best Practices for Security, Identity, & Compliance.
* *Intel Software Developer's Manual* - Basic Architecture and Protection Rings.