# Clase: Criptografía Aplicada al Voto Electrónico (Eje 3)

## 📌 Contexto de la Sesión

- **Estado de la plataforma:** Presentó caídas durante la tarde, pero las **notas ya están publicadas** (el profesor felicita a quienes dieron la "milla extra" configurando PGP/MIME y Thunderbird en el laboratorio anterior).
    
- **Temática principal:** Inicio del **Eje 3**, enfocado en la viabilidad, problemas y fundamentos criptográficos del **voto electrónico** frente al sistema convencional manual.
    

---

## 🔒 La Clave Tecnológica: Criptografía en el Voto Electrónico

El núcleo técnico de la clase consistió en explicar cómo la criptografía resuelve los retos de seguridad y anonimato en un sistema electoral digital.

### 1. Mecanismos de Cifrado

- **Cifrado Simétrico:** Se utiliza para la **identificación plena del votante** mediante algoritmos robustos como **SHA-256** o **SHA-512** incluidos en las papeletas/tarjetas asignadas.
    
- **Cifrado Asimétrico (Llave Pública y Privada):** Se implementa mediante algoritmos tipo **RSA** y criptografía de curvas elípticas (**ECC**) basadas en funciones **SHA-3** para asegurar que el voto sea único, inalterable y no falsificable.
    

### 2. Infraestructura y Seguridad del Dato

- **Blockchain (Modo CBC):** La contabilización y transición de los votos se estructura bajo un libro digital descentralizado y asegurado con firmas digitales para evitar la manipulación del conteo final.
    
- **Técnica de _Salting_ (Clave del Secreto):** Técnica criptográfica crucial que **separa la identidad del votante de la opción por la cual votó**. Funciona en una sola vía lineal; no hay forma de volver a conectar al ciudadano con su voto una vez procesado.
    
- **Biometría:** Uso de lectores de huella integrados para mitigar la suplantación y la doble votación en tiempo real.
    

---

## 🗺️ El Voto Electrónico en el Mundo (Modelos y Ejemplos)

El profesor expuso tres modalidades del voto electrónico:

1. **Papeletas precifradas / Tarjetas:** Se procesan en urnas con escáneres electrónicos (Caso España).
    
2. **Máquinas de Grabación Electrónica Directa (DRE):** Botones físicos o pantallas táctiles (Caso Brasil e India, este último operando el sistema más grande del mundo con hardware solar).
    
3. **Voto por Internet (En línea):** Validaciones con identidad digital y PIN de doble factor (Caso Estonia, donde más del 51% vota digitalmente).
    

---

## 🔎 Análisis del Caso Colombia: Retos y Leyes

A pesar de que el marco legal existe desde hace décadas, los detractores y expertos argumentan tres grandes limitantes para su adopción total:

- **Económico:** El voto manual cuesta alrededor de $2.6 billones, mientras que implementar el voto electrónico se estima en **$10.5 billones** (incluyendo costos por mesa y biometría).
    
- **Orden Público e Infraestructura:** Riesgo en el traslado de máquinas a zonas rurales y una **infraestructura de telecomunicaciones muy débil** para garantizar la transmisión en tiempo real.
    
- **Logística:** Falta de capacidad de la Registraduría, la cual requeriría formar a más de 204,000 nuevos delegados técnicos.
    

> [!NOTE] **El Dato Histórico** En Colombia el voto electrónico está respaldado en el papel por la **Ley 892 de 2004** y la **Ley 1475 de 2011**. Ambas proyectaban su uso para comicios pasados, pero debido a la falta de voluntad política y recortes presupuestales (como la reducción del 28% del presupuesto electoral), sigue sin ejecutarse en la práctica.

---

## 📋 Tareas, Compromiso y Modalidad de Trabajo

Hacia el final del audio (minuto 56:45), el estudiante Fabio interviene para aclarar los detalles de la entrega del Eje 3:

> [!IMPORTANT] **Detalles de la Asignación**
> 
> - **¿El trabajo es solo o en pareja?:** El trabajo es **estrictamente INDIVIDUAL**.
>     
> - **Formato:** Se entregará un **documento escrito** (análisis y síntesis).
>     
> - **Contenido clave:** Identificación de los elementos criptográficos aplicados en el voto electrónico expuestos en la sesión.
>     
> - **Estado de publicación:** El profesor la habilitará en la plataforma una vez se estabilice el sistema.
>     

### 🎯 Tareas Sorpresa / Próxima Semana

- **No hay tareas sorpresa complejas para ya.** El profesor enfatizó que la asignación no es tan complicada como la que sugería la plataforma originalmente.
    
- **Compromiso próximo:** La siguiente clase se trabajará de forma práctica utilizando un **simulador de voto electrónico**. El entregable escrito se podrá consolidar y sacar adelante la próxima semana sin contratiempos.