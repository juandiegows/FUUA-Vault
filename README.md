Esta es la Documentacion del mis clases


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

