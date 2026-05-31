
# Clase: Simulación de Voto Electrónico y Compresión de Datos aplicada a la Criptografía (Eje 3)

## 📌 Contexto de la Sesión

- **Grabaciones disponibles:** El profesor confirma que los problemas de la plataforma se solucionaron y las clases anteriores ya están accesibles.
    
- **Dinámica:** Sesión dividida en dos bloques: la guía práctica para completar la actividad individual de la urna electrónica y la explicación teórica de por qué la compresión es indispensable en entornos criptográficos.
    

---

## 🗳️ Guía de la Actividad Práctica (Urna Electrónica)

El profesor mostró diferentes alternativas de **simuladores de urnas electrónicas** (basados en los sistemas reales de España, Brasil, Argentina y Paraguay) donde se combinan papeletas impresas, códigos de barras/flechas de dirección y pantallas táctiles.

> [!PRACTICAL] **Instrucciones de la Actividad**
> 
> - **Uso de simulador (Opcional pero recomendado):** Descargar una app de simulación de urna electrónica en Google Play o usar versiones web para hacer un ejercicio simulado en casa (ej. votaciones familiares usando el mes de las madres como temática).
>     
> - **Objetivo de análisis:** Identificar de forma analítica en qué fases del flujo de la app/simulador se aplican los pilares de la seguridad informática: **Confidencialidad, Autenticidad, No repudio, Integridad y Anonimato**.
>     
> - **Formato de entrega:** Documento escrito individual a entregar el **próximo lunes**.
>     

### 🌟 Los 5 Puntos Extra: Proyecto Votec

Para obtener los puntos adicionales de la actividad, se debe investigar el funcionamiento del proyecto **Votec** (Sistema de Votación Electrónica Ciudadana).

- **Origen:** Diseñado por el **IDEPAC** (Instituto Distrital de Participación y Acción Comunal) en la alcaldía de Bogotá.
    
- **Uso:** Implementado entre 2022 y 2023 para votaciones comunales y acciones populares locales, integrando tecnología en procesos de participación ciudadana.
    

---

## 📉 Teoría: Relación entre Compresión de Datos y Criptografía

El núcleo teórico de la clase abordó un **efecto no deseado de la criptografía**: el incremento crítico del tamaño de los mensajes cifrados.

### El Problema del Tamaño de la Cifra

Al aplicar algoritmos de cifrado (como AES-128/256) combinados con funciones Hash para la transmisión de llaves y firmas digitales, un texto en claro corto crece exponencialmente en bytes sobre la red.

```
[Texto en Claro: 24 Bytes] ➡️ [Algoritmo AES + Hash] ➡️ [Texto Cifrado en Red: ~151 Bytes]
*(En este ejemplo, el tamaño final se incrementó casi 7 veces)*
```

Este fenómeno satura el **ancho de banda**, el cual sigue siendo un recurso finito y un cuello de botella sistémico (provocando caídas históricas de infraestructura en días pico como fines de año o colapsos de aplicaciones como la de Bancolombia).

### La Solución: Compresión Previa al Cifrado

Para mitigar esto, los sistemas modernos aplican un algoritmo de compresión **al texto en claro ANTES de ser procesado por el motor criptográfico**.

---

## 🛠️ Tipos de Algoritmos de Compresión

Los algoritmos analizados se dividen estrictamente en dos categorías según la naturaleza del dato:

### 1. Compresión Con Pérdida (_Lossy_)

- **Mecanismo:** Elimina selectivamente píxeles o frecuencias de audio redundantes que el ojo o el oído humano no perciben fácilmente a simple vista.
    
- **Uso principal:** Tratamiento de imágenes, video y sonido (Formatos como `JPG`, `MP4`, transmisiones de YouTube a diferentes tasas de Kbps, o formatos de audio espacial/4K).
    
- **Impacto:** Reduce drásticamente el peso del archivo sacrificando fidelidad sutil, ideal para streaming o esteganografía.
    

### 2. Compresión Sin Pérdida (_Lossless_)

- **Mecanismo:** Recorre el flujo de datos eliminando redundancias sintácticas (espacios en blanco, comas, saltos de línea) y codificando las repeticiones (ej. transformar una cadena repetida en un índice del tipo `A8 B6 C12`).
    
- **Uso principal:** Textos, bases de datos, código fuente y **mensajería criptográfica**. Permite recuperar el 100% del archivo original tras aplicar la función inversa (descompresión).
    

---

## 📊 Comparativa de Formatos y Sistemas de Archivos

El profesor analizó el rendimiento de las herramientas de compresión a nivel de usuario y sistemas distribuidos:

|**Algoritmo / Formato**|**Características Técnicas**|**Entorno Común**|
|---|---|---|
|**WinRAR (`.rar`)**|El estándar líder. Alta velocidad de procesamiento, uso optimizado de memoria RAM y capacidad exclusiva de **fragmentar datos en volúmenes encadenados**.|Windows (Usuario final/Pago)|
|**7-Zip (`.7z`) / ZIP**|Código abierto y alta compatibilidad. ZIP procesa muy rápido pero con menores tasas de compresión que RAR.|Multiplataforma|
|**`.cab` (Cabinet)**|Archivos comprimidos nativos para empaquetado de componentes.|Instalaciones de Windows|
|**`.tar.gz` / `.bz2`**|Compresión nativa mediante empaquetamiento y compresión secuencial.|Linux (Instalación y compilación de paquetes)|

> [!💡] **Conclusión del Eje 3**
> 
> La compresión de datos es un componente **implícito e indivisible** de la criptografía moderna. Sin ella, la infraestructura global de telecomunicaciones colapsaría bajo el peso de los metadatos de seguridad, firmas y cifrados necesarios para proteger la privacidad digital.

---

## 🔮 Compromiso para el Cierre (Próxima Semana)

- **Tema entrante:** Inicio del último eje temático enfocado en **Blockchain**.
    
- **Práctica:** Se trabajará en la próxima sesión con simuladores interactivos de bloques y cadenas distribuidas.