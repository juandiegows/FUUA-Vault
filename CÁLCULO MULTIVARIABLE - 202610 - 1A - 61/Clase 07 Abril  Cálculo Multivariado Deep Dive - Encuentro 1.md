
**Docente:** Silvia Vega Riaño | **Grupo:** 61

**Asignatura:** Ciencias Básicas - Areandina

---

## 🏗️ Estructura y Reglas del "Runtime" (Metodología)

|**Componente**|**Detalle**|
|---|---|
|**Paradigma de Entrega**|Todo lo matemático debe ser **Legacy Style** (puño y letra). Escaneado y embebido en Word.|
|**Middleware de Comunicación**|Mensajería Canvas (único canal oficial para dudas y link de tutorías).|
|**Unit Testing (Asistencia)**|Formularios al final de la clase. Valen **5 puntos/eje**. Si faltas, tienes hasta el lunes siguiente a las 18:00 para pedir el link (previa visualización del video).|
|**Control de Versiones (Grabaciones)**|Se publican en el Foro de Canvas apenas Google Meet procese el video.|

---

## 🧠 Core Theory: De una Variable a Varias

### 1. El Salto de Dimensión

Hasta ahora, en Cálculo Diferencial e Integral, trabajabas en $\mathbb{R}^1 \rightarrow \mathbb{R}^1$ (una entrada, una salida). Ahora entramos en el terreno de las **Funciones Vectoriales**, donde un escalar (usualmente el tiempo $t$) genera un vector en el espacio.

### 2. Definición Formal de Función Vectorial

Una función vectorial $r(t)$ en el espacio es una función cuyos componentes son funciones escalares:

$$r(t) = \langle f(t), g(t), h(t) \rangle = f(t)\mathbf{i} + g(t)\mathbf{j} + h(t)\mathbf{k}$$

- **Dominio:** Todos los valores de $t$ para los cuales todas las funciones componentes ($f, g, h$) están definidas.
    
- **Vectores Unitarios:**
    
    - $\mathbf{i}$ : Vector dirección en el eje $X$ (1,0,0).
        
    - $\mathbf{j}$ : Vector dirección en el eje $Y$ (0,1,0).
        
    - $\mathbf{k}$ : Vector dirección en el eje $Z$ (0,0,1).
        

### 3. Ecuaciones Paramétricas

Es la forma de "desacoplar" el vector en sus componentes individuales. Si tenemos una partícula moviéndose en el espacio, su posición en cualquier momento $t$ se define por:

- $x = f(t)$
    
- $y = g(t)$
    
- $z = h(t)$
    

---

## ✍️ Análisis del Ejercicio Práctico

La profe Silvia explicó cómo encontrar un punto específico en la trayectoria de una recta.

**Input:** $r(t) = (3 - t)\mathbf{i} - (2 - 2t)\mathbf{j} + (1 + 3t)\mathbf{k}$

**Extracción de Ecuaciones:**

1. $x(t) = 3 - t$
    
2. $y(t) = -2 - 2t$ (Ojo con el signo negativo fuera del paréntesis)
    
3. $z(t) = 1 + 3t$
    

**Cálculo del Punto Inicial ($t = 0$):**

Reemplazamos el parámetro $t$ por $0$ en cada ecuación:

- $x(0) = 3 - 0 = 3$
    
- $y(0) = -2 - 2(0) = -2$
    
- $z(0) = 1 + 3(0) = 1$
    

**Resultado:** El punto de inicio de esta trayectoria en el espacio es el vector de posición **$P_0(3, -2, 1)$**.

---

## 🚀 Sprint 1: Actividad Evaluativa (Eje 1)

Como futuro ingeniero, debes aplicar esto a tu carrera. Aquí te doy unas ideas de **Contexto**:

- **Computación Gráfica:** Definir la trayectoria de una cámara en una escena 3D.
    
- **Robótica:** Programar el movimiento del brazo de un robot (Cinemática).
    
- **Videojuegos:** Calcular el desplazamiento de un proyectil afectado por variables externas.
    

### Pipeline de Entrega:

1. **Identificar Contexto:** ¿Dónde aplicarás la función vectorial?
    
2. **Modelado Matemático (A mano):** Plantea la función $r(t)$ y sus componentes.
    
3. **Resolución (A mano):** Muestra el paso a paso de cómo se comporta la función.
    
4. **Data Viz (Infografía con IA):** Usa herramientas como Canva (con Magic Design) o Gamma para generar la infografía. Debe incluir tu nombre y ser muy visual.
    

---

### 📌 Recordatorios de la Profe:

- **Cero tolerancia** con Editores de Ecuaciones (quieren ver tu proceso mental en papel).
    
- Los trabajos colaborativos empiezan en el **Eje 2**. Todos los integrantes del grupo deben subir el archivo a Canvas, no solo uno.
    
- Asegúrate de aceptar la invitación en el **Google Calendar** con tu correo de Areandina para evitar problemas de permisos con los videos.
    

---

#Etiquetas: #CalculoMultivariado #IngenieriaDeSistemas #FuncionesVectoriales #EcuacionesParametricas #Areandina2026