
**Fecha de la clase:** 13 de abril de 2026 (aproximada, según entrega el 20 de abril)

**Tema principal:** Funciones Vectoriales y Dominio

**Eje:** Actividad Evaluativa Eje 1

---

## 🗓️ Pendientes y Entregas

> [!IMPORTANT] **Actividad Evaluativa Eje 1**
> 
> - **Fecha límite:** Lunes, 20 de abril, 18:00 (6:00 PM).
>     
> - **Requisitos obligatorios:**
>     
>     - **Parte 2 y 3:** Deben realizarse **a mano (puño y letra)**, escaneadas y subidas. No se acepta editor de ecuaciones.
>         
>     - **Contenido:** Planteamiento de una función vectorial aplicada a un contexto profesional o laboral.
>         
>     - **Formato:** Documento Word que incluya la infografía, las referencias bibliográficas y el desarrollo manual.
>         
> - **Asistencia:** Enviar correo por Canvas si se ve la grabación para recibir el link de participación (máximo lunes 18:00).
>     

---

## 🧠 Repaso: Funciones Vectoriales

Las funciones vectoriales relacionan un número real (parámetro $t$) con un vector en el espacio.

- **Dominio:** Conjunto de números reales ($t$) que no indefinen la función.
    
- **Rango:** Conjunto de vectores resultantes.
    
- **Representación:** Pueden ser en 2D $(X, Y)$ o 3D $(X, Y, Z)$.
    
- **Variable:** Generalmente el tiempo ($t$).
    

---

## ✍️ Ejercicio Práctico: El Insecto en la Hélice

**Enunciado:** Un insecto sigue una trayectoria en un alambre con forma de hélice dentro de un globo de radio $10$.

**Vector posición:**

$$r(t) = \langle 6 \cos(\pi t), 6 \sin(\pi t), 2t \rangle$$

### 1. Ecuaciones Paramétricas

A partir del vector posición:

- $x(t) = 6 \cos(\pi t)$
    
- $y(t) = 6 \sin(\pi t)$
    
- $z(t) = 2t$
    

### 2. Ecuación de la Trayectoria (Cilindro)

Usando la identidad $\sin^2\theta + \cos^2\theta = 1$:

$$x^2 + y^2 = (6 \cos(\pi t))^2 + (6 \sin(\pi t))^2$$

$$x^2 + y^2 = 36$$

### 3. Punto de Choque con el Globo ($R=10$)

El globo tiene la ecuación $x^2 + y^2 + z^2 = R^2$.

1. Sustituimos $x^2 + y^2 = 36$ y $R = 10$:
    
    $$36 + z^2 = 100$$
    
2. Sustituimos $z = 2t$:
    
    $$36 + (2t)^2 = 100 \implies 4t^2 = 64 \implies t^2 = 16 \implies \mathbf{t = 4}$$
    
3. **Coordenadas del choque ($t=4$):**
    
    - $x = 6 \cos(4\pi) = 6(1) = \mathbf{6}$
        
    - $y = 6 \sin(4\pi) = 6(0) = \mathbf{0}$
        
    - $z = 2(4) = \mathbf{8}$
        
        **Punto de impacto:** $(6, 0, 8)$
        

---

## 📹 Análisis de Dominio (Video)

Para hallar el dominio de una función vectorial $r(t) = \langle f(t), g(t), h(t) \rangle$, se deben interceptar las restricciones de cada componente:

|**Componente**|**Ejemplo de Restricción**|**Razón**|
|---|---|---|
|**I (Racional)**|$t + 2 \neq 0$|El denominador nunca puede ser cero ($t \neq -2$).|
|**J (Trigonométrica)**|$\sin(t)$|Dominio en todos los reales ($-\infty, \infty$).|
|**K (Logarítmica)**|$\ln(9 - t^2)$|El argumento debe ser mayor a cero ($9 - t^2 > 0$).|

---

## 🔗 Recursos Adicionales

- **Ubicación de grabaciones:** Sección de Foros -> Link de grabaciones encuentros sincrónicos.
    
- **Grupo:** 61.
    

---

#calculo-multivariable #universidad #resumen-clase #areandina