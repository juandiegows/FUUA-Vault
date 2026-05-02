# Documentación de Mis Clases

Esta es la documentación completa de mis clases y recursos educativos.

```
const bloques = document.querySelectorAll('div[aria-label^="Segmento que empieza"]');
const transcripcion = Array.from(bloques)
    .map(b => {
        const label = b.getAttribute('aria-label');
        // Limpiamos el prefijo "Segmento que empieza en el X:XX: "
        return label.replace(/^Segmento que empieza en el \d+:\d+:\s*/, '').trim();
    })
    .filter(t => t !== "")
    .join('\n');

if (transcripcion) {
    console.log(transcripcion);
    copy(transcripcion);
    console.log("%c ¡Texto recuperado y copiado! ", "background: green; color: white");
} else {
    console.error("No se detectaron segmentos. Prueba a bajar con el scroll hasta el final de la transcripción primero.");
}
```

```
(async function() {
    const config = {
        selectorBloques: 'div[aria-label^="Segmento que empieza"]',
        regexTiempo: /^Segmento que empieza en el ([\d:]+):\s*/i,
        ruido: "Copiar enlace en esta transcripción",
        msEspera: 450, 
        distanciaScroll: 600
    };

    const scroller = document.querySelector('div[jsname="goZYA"]') || document.querySelector('div.Ahjque');

    if (!scroller) {
        return console.error("❌ No se encontró el área de scroll.");
    }

    console.log("%c ⏳ Cargando... No cierres la consola ni cambies de pestaña. ", "background: #222; color: #bada55;");

    let ultimaPos = -1;
    let acumulado = 0;
    while (scroller.scrollTop !== ultimaPos) {
        ultimaPos = scroller.scrollTop;
        scroller.scrollTop += config.distanciaScroll;
        acumulado++;
        let espera = (acumulado % 10 === 0) ? 1200 : config.msEspera;
        await new Promise(r => setTimeout(r, espera));
    }

    const bloques = document.querySelectorAll(config.selectorBloques);
    const lineas = Array.from(bloques)
        .map(b => {
            const label = b.getAttribute('aria-label') || "";
            if (label.includes(config.ruido)) return null;
            const match = label.match(config.regexTiempo);
            if (match) {
                return `**[${match[1]}]** ${label.replace(config.regexTiempo, '').trim()}`;
            }
            return null;
        })
        .filter(t => t !== null);

    const transcripcionFinal = lineas.join('\n');

    if (transcripcionFinal) {
        console.log("%c --- TRANSCRIPCIÓN LISTA --- ", "background: blue; color: white;");
        console.log(transcripcionFinal);
        
        console.log("%c ⚠️ ¡ATENCIÓN! Haz CLIC en cualquier parte de la página (fuera de la consola) AHORA para permitir el copiado... ", "background: red; color: white; font-weight: bold; padding: 5px;");
        
        // Esperamos 3 segundos para que hagas clic en la página
        await new Promise(r => setTimeout(r, 3000));

        try {
            await navigator.clipboard.writeText(transcripcionFinal);
            console.log("%c 🚀 ¡TODO COPIADO AL PORTAPAPELES! ", "background: green; color: white; padding: 8px;");
        } catch (err) {
            console.error("❌ Fallo el copiado automático:", err);
            console.log("%c Selecciona el texto de arriba manualmente. ", "background: orange;");
        }
        
        scroller.scrollTop = 0; 
    }
})();
```


Si quieres que Gemini, ChatGPT o cualquier IA te genere un resumen perfecto para tu flujo de trabajo en **Obsidian**, necesitas un prompt que le dé estructura de base de datos personal.

Como sé que te gusta el **Clean Architecture** y eres **Full-stack**, este prompt está diseñado para que la IA organice la información de forma técnica y jerárquica.

Copia y pega esto:

---

### 📝 El Prompt Maestro

**Actúa como un Investigador Académico y Arquitecto de Software Senior.** Tu objetivo es transformar una transcripción de clase en una **Guía de Estudio Exhaustiva** para mi Obsidian.

**Instrucciones de Proceso:**

1. **Análisis de Transcripción:** Extrae los conceptos clave, pero no te quedes solo con lo que dice el profesor.
    
2. **Investigación Externa:** Para cada concepto técnico (ej. Kernel, Arquitectura Harvard, Redes P2P), busca información actualizada en internet y añade detalles técnicos que no estén en el texto (ej. diferencias actuales entre Ring 0 y Ring 3, o cuellos de botella en CPUs modernas).
    
3. **Estructura Requerida:**
    
    - **YAML Frontmatter:** Incluye metadata completa.
        
    - **Encabezados Jerárquicos:** Usa `#` para el título y `##` para secciones principales.
        
    - **Deep Dive Técnico:** Crea una sección extensa por cada tema principal donde expliques el "Cómo" y el "Por qué" desde una perspectiva de Ingeniería.
        
    - **Sección de Referencias:** Al final, añade una lista de enlaces o bibliografía sugerida (Documentación oficial, Whitepapers).
        
    - **Tracking de Tareas y Reglas:** Mantén los Callouts de `[!SUCCESS]`, `[!IMPORTANT]` y `[!WARNING]`.
        

**Reglas de Formato:**

- Genera el resultado final en un bloque de código Markdown.
    
- Usa tablas comparativas detalladas.
    
- **EXTENSIÓN:** Sé detallado. Si el profesor menciona "Kernel", explica su gestión de memoria, planificación de procesos y seguridad.
    

**Contenido de la clase:**