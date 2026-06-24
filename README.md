# PitchCraft Interactive

Aplicación web de una sola página (PWA) para **construir, visualizar, practicar y compartir** una pieza de comunicación estructurada en cinco fases temporizadas. Pensada como herramienta pedagógica del curso de **Infografía**, aplica la metodología **AIDA+Close** (Hook → Interés → Deseo → Acción → Cierre) al diseño de información.

- **Archivo único:** `pitchcraft.html` (~123 KB), todo embebido.
- **Funciona offline / desde `file://`:** no requiere servidor ni instalación. Basta abrir el archivo en el navegador.
- **Sin dependencias de runtime críticas:** los íconos son SVG inline; solo Bootstrap CSS y las fuentes se cargan por CDN (degradan de forma aceptable sin red).

---

## Uso rápido

1. Abre `pitchcraft.html` en un navegador moderno (Chrome, Edge, Firefox, Safari).
2. Ve a **Construir** y completa el **Registro del estudiante** (nombres, apellidos, correo).
3. Pulsa **Insertar demo guiado** para ver un ejemplo modelo en cada campo, o empieza desde cero.
4. Completa los campos del proyecto; el panel de vista previa se actualiza en vivo.
5. Pasa a **Visualizar** para ver la infografía por fases, y a **Practicar** para ensayar con cronómetro.
6. Usa **Generar prompt de optimización** para obtener un prompt listo para refinar tu infografía con una IA.
7. Usa **Generar prompt de video** para obtener un prompt con la misma estructura AIDA+Close, pero orientado a **producir un video pitch** (guion técnico por fase + prompt listo para una IA de generación de video).
8. Usa **Informe PDF / .md / .csv** para descargar toda la información del formulario como informe de entrega para el docente (el PDF abre la vista de impresión del navegador → *Guardar como PDF*).
9. En cada campo del formulario, pulsa el botón **IA** (junto a la etiqueta) para obtener un prompt adaptado a ese campo: cópialo y pégalo en tu asistente de IA junto con el **PDF del informe Co-STORM** para extraer automáticamente esa información.

---

## Secciones

| Sección | Función |
|---|---|
| **Inicio** | Presentación, robot mecatrónico animado, cronómetro de referencia y accesos directos. |
| **Construir** | Registro del estudiante, demo guiado, perfil de audiencia con ponderaciones, 7 bloques estructurales, generador de prompt y fundamentación metodológica. |
| **Visualizar** | Infografía interactiva, radar de audiencia y modo presentación a pantalla completa. |
| **Practicar** | Cronómetro circular que cambia de color por fase, modos de ensayo, grabación por micrófono, **locución del pitch por voz (text-to-speech)** generada desde el formulario, e historial. |
| **Compartir** | URL, código QR, embed e instalación como PWA. |

---

## Las cinco fases (AIDA+Close)

| Fase | Propósito |
|---|---|
| **HOOK** | Captar la atención en los primeros segundos. |
| **INTERÉS** | Exponer el problema y generar relevancia. |
| **DESEO** | Construir valor: solución, propuesta y diferenciadores. |
| **ACCIÓN** | Llamar a un paso concreto. |
| **CIERRE** | Retomar la idea-fuerza y cerrar con impacto. |

Las ponderaciones de cada fase se ajustan según la audiencia seleccionada (inversor, cliente, socio o personalizado).

---

## Privacidad y datos

Todos los datos se guardan **localmente en el navegador** (`localStorage`); no se envían a ningún servidor. Las claves utilizadas son:

- `pitchcraft_student` — datos de registro del estudiante.
- `pitchcraft_pitches` — proyectos/infografías guardados.
- `pitchcraft_history` — historial de ensayos de práctica.

Para borrar los datos, limpia el almacenamiento del navegador para este archivo.

**Compartir (sin servidor):** la sección *Compartir* genera una URL que **lleva el pitch codificado en el fragmento `#p=`** (base64). No hay backend: al abrir el enlace, la app decodifica y carga el pitch automáticamente. Por eso las métricas de aperturas/tiempo/dispositivos son una demostración (requieren un servidor de analítica) y solo el *Pitch Score* se calcula localmente. El **código QR** se renderiza con un servicio externo (`api.qrserver.com`) a partir de esa URL pública; si no hay conexión, usa el botón *Copiar*.

---

## Notas técnicas

- **PWA / Service Worker:** el registro del service worker solo se intenta bajo `http(s)`. Desde `file://` no se registra (es esperado) y la app sigue funcionando; la instalación PWA y el cacheo offline automático requieren servir el archivo por HTTPS. La app incluye `manifest.json` e iconos (`icon-192.png`, `icon-512.png`) para ser **instalable** como PWA (botón «Instalar App» cuando el navegador lo permite).
- **Identidad visual:** sistema d3magindesign — navy `#1B2A4A`, naranja `#E8621A`, crema `#F5F0E8`; tipografías Syne + DM Sans + DM Mono. Capa visual mecatrónica (grid HUD, robot SVG animado, íconos line-style).
- **Generador de prompt:** construye el texto del prompt combinando los datos del proyecto, la audiencia y las ponderaciones; **no** llama a ninguna IA por sí mismo (se copia y se pega donde se desee). Existen dos variantes: *optimización de infografía* y *video pitch*. La variante de optimización permite elegir **dónde se aplicará el resultado** (HTML, PowerPoint/Slides, Canva o imagen) e incluye instrucciones y herramientas para ese destino. La variante de video añade parámetros de producción (duración, aspecto, plataforma, estilo, narración, tono) y la **herramienta de IA de video recomendada** (Sora, Runway, Veo, Kling, Pika, Luma, Higgsfield, inVideo AI, CapCut; las de instrucción única como inVideo/CapCut reciben una instrucción única en lugar de prompts por clip), además de un storyboard por fase y un prompt condensado por escena.
- **Autoguardado del formulario:** todos los campos de *Construir* se guardan automáticamente en `localStorage` (`pitchcraft_build`) y se restauran al recargar, de modo que los datos siempre están disponibles para generar prompts, informes y la visualización.

---

## Fundamentación metodológica

La estructura y el flujo se apoyan en marcos consolidados (referencias completas y verificables dentro de la propia app, sección *Fundamentación metodológica*):

- Modelo AIDA (Lewis, 1898; Strong, 1925).
- Narrativa de presentación (Duarte, 2010).
- Diseño de información y carga cognitiva (Tufte, 1990; Mayer, 2009).
- Aprendizaje experiencial (Kolb, 1984).
- Práctica deliberada (Ericsson, Krampe & Tesch-Römer, 1993).

> Verifica cada referencia y adáptala al estilo de citación de tu curso antes de incluirla en un entregable formal.

---

## Créditos

**Docente:** Mg. Mario Quiroz · **Curso:** Infografía · 2026 — Semana 14
Marca: d3magindesign.
