# VoiceOver App

PWA de texto a voz (text-to-speech) instalable, con descarga de audio. Todo corre en el navegador, sin backend ni API externa.

## Funcionalidades

- **Generar voz** a partir de cualquier texto, usando las voces del sistema disponibles en el navegador (`SpeechSynthesis`), con control de velocidad y tono.
- **Lectura natural**: el texto se divide en oraciones y fragmentos, variando tono y ritmo según signos de exclamación, preguntas, mayúsculas y pausas entre párrafos, para que no suene tan robótico como una lectura plana.
- **Reproductor** con play/pausa, detener y barra de progreso estimada.
- **Descarga de audio**: graba la síntesis de voz con `MediaRecorder` y la descarga como `.webm`/`.ogg`. Si el navegador no permite capturar el audio generado (limitación conocida de `SpeechSynthesis` en algunos navegadores), cae automáticamente a descargar el texto en `.txt`.
- **Historial** de las últimas 50 generaciones (texto, voz, velocidad, tono), guardado en `localStorage`, con opciones de reproducir, editar o borrar cada una.
- **Instalable como PWA** (manifest + íconos, funciona offline ya que no depende de red).

## Cómo usarlo

Abrir `index.html` en un navegador con soporte de síntesis de voz (Chrome o Safari recomendados). No requiere instalación ni servidor.

## Stack

HTML, CSS y JavaScript vanilla. Sin frameworks ni dependencias externas. APIs del navegador: `SpeechSynthesis` (texto a voz) y `MediaRecorder`/`AudioContext` (grabación).

## Limitación conocida

La descarga de audio depende de poder enrutar la salida de `SpeechSynthesisUtterance` hacia un `AudioContext`, algo que no todos los navegadores permiten de forma directa. Cuando eso falla, la app lo detecta y ofrece el texto como `.txt` en su lugar, en vez de entregar un archivo de audio silencioso.
