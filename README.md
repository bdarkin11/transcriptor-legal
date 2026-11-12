# Transcriptor Legal con IA

Aplicacion web de una sola pagina para transcribir audio de contenido juridico con Gemini. Resuelve el problema tipico de la transcripcion automatica en derecho: los terminos tecnicos mal reconocidos. Los corrige con un diccionario propio (por ejemplo "a vias corpus" → "hábeas corpus") y aprende correcciones nuevas, que se guardan en Firestore.

## Live Deployment

> **Live URL:** `[AGREGAR URL DE VERCEL / FIREBASE HOSTING]`

## Funciones

- Transcripcion con la API de Gemini.
- Diccionario de terminos juridicos con correcciones compartidas en Firestore.
- Guardado automatico del trabajo en curso y archivo de transcripciones en el navegador (localStorage).

## Tech Stack

HTML · CSS · JavaScript (ES modules) · Google Gemini API · Firebase Firestore

## Agentic Workflow

Este proyecto se construyo con desarrollo asistido por IA (Claude), con el autor dirigiendo, revisando y aprobando cada cambio.

- **Arquitectura de contexto:** una sola pagina sin build ni backend, con la logica separada en transcripcion, diccionario de correcciones y persistencia.
- **Directivas de seguridad:** ninguna credencial vive en el codigo. Antes de publicar se audito el repo completo (claves, tokens, rutas locales y datos de cuenta) y las claves se movieron a un `config.js` excluido por `.gitignore`, con `config.example.js` como plantilla.
- **Testing:** se valido manualmente con audios reales y scripts de prueba contra la API. Todavia no hay una suite de tests automatizados; es el siguiente paso pendiente.

## Local Setup

1. Copiar `config.example.js` como `config.js` y completar la API key de Gemini y la configuracion de Firebase.
2. Poner las imagenes de fondo en `img/` (`fondo_1.png` a `fondo_5.png`).
3. Abrir `index.html` con un servidor local (por ejemplo la extension Live Server).

Al ser una app sin backend, la key de Gemini queda visible para quien abra la pagina: antes de publicarla conviene restringir la key por dominio en Google Cloud o pasar las llamadas por un backend.
