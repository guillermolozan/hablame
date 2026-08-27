# LEELO

App web de un solo archivo (`index.html`) que convierte tu voz en texto grande en pantalla. Pensada para mostrar mensajes en el celular: presiona, habla, y lo dicho aparece con tipografía gigante y auto-ajustada.

**En línea**: https://leelo.info (también en https://guillermolozan.github.io/hablame/)

## Uso

Abre `index.html` en **Chrome** (Android/escritorio) o **Safari (iOS 17+)**. No requiere instalación ni servidor; si el permiso de micrófono falla desde `file://`, sírvelo localmente:

```sh
python3 -m http.server
```

Firefox no es compatible (no tiene Web Speech API).

## Funciones

- **Afirmar**: dicta un enunciado; lleva punto final automático.
- **Preguntar**: fuerza el formato de pregunta sin detección.
- Puntuación automática por silencio (punto y salto de línea configurables) y detención automática tras silencio.
- Ajustes: temas de color y colores personalizados, tamaño de texto auto/manual, tipografía, mayúsculas, idioma de reconocimiento (`es-PE` por defecto), mantener pantalla encendida.
- Responder escribiendo: muestra cualquier texto escrito en grande.
- Historial de los últimos 12 mensajes (localStorage).

## Notas técnicas

Todo vive en `index.html` — HTML, CSS y JS, sin build ni dependencias. La persistencia usa localStorage con respaldo en memoria si no está disponible. El ajuste de texto usa búsqueda binaria sobre el tamaño de fuente.
