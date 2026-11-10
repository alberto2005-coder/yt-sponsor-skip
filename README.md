# YT Sponsor Skip

[Español](#español) · [English](#english)

---

## Español

### Índice

- [Descripción](#descripción)
- [Características](#características)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Configuración](#configuración)
- [Privacidad](#privacidad)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Desarrollo](#desarrollo)
- [Licencia](#licencia)

### Descripción

Extensión de navegador que **detecta y salta automáticamente los segmentos patrocinados** de los vídeos de YouTube. Utiliza la transcripción del vídeo y un modelo de lenguaje de [Groq](https://groq.com/) para localizar las menciones publicitarias y ofrecer un botón para omitirlas.

Compatible con **Chrome, Edge y Firefox** mediante Manifest V3.

### Características

- **Detección inteligente de sponsors** con el modelo `llama-3.3-70b-versatile` de Groq.
- **Botón «Skip Sponsor»** superpuesto en el reproductor cuando se detecta un patrocinio.
- **Panel de confirmación** para revisar el segmento antes de saltarlo.
- **Panel de transcripción** con los fragmentos analizados.
- **Validación de timestamps** para evitar saltos incorrectos.
- **Configuración local**: la API key se guarda únicamente en el almacenamiento del navegador.
- **Compatible con Chrome y Firefox** desde el mismo código base.

### Requisitos

- Una cuenta en [Groq](https://console.groq.com/) y una **API key** que empiece por `gsk_`.
- Chrome/Edge 109+ o Firefox 109+.

### Instalación

#### Chrome / Edge

1. Descarga o clona este repositorio.
2. Abre `chrome://extensions/` (o `edge://extensions/`).
3. Activa el **Modo de desarrollador**.
4. Pulsa **Cargar descomprimida** y selecciona la carpeta del proyecto.
5. Abre YouTube y pulsa el icono de la extensión para configurar tu API key.

#### Firefox

1. Abre `about:debugging#/runtime/this-firefox`.
2. Pulsa **Cargar complemento temporal**.
3. Selecciona el archivo `manifest.json`.

### Configuración

1. Pulsa el icono de **YT Sponsor Skip** en la barra del navegador.
2. Introduce tu **Groq API Key** (`gsk_...`).
3. Pulsa **Guardar** o **Probar conexión**.
4. Abre cualquier vídeo de YouTube: la extensión analizará la transcripción y mostrará el botón de salto cuando encuentre un patrocinio.

### Privacidad

- La **transcripción del vídeo se envía a la API de Groq** para su análisis. No se envía a ningún servidor propio.
- La API key se almacena localmente en `browser.storage.local` y nunca se comparte con terceros.
- La extensión no recopila estadísticas ni telemetría.

### Estructura del proyecto

```text
yt-sponsor-skip/
├── manifest.json     Configuración de la extensión (Manifest V3)
├── background.js     Service Worker: llamadas a Groq y validación
├── content.js        Lógica inyectada en YouTube: DOM, transcripción y salto
├── content.css       Estilos del botón y los paneles en YouTube
├── popup.html        Interfaz de configuración
├── popup.css
├── popup.js
└── icons/            Iconos de la extensión
```

### Desarrollo

No requiere compilación ni dependencias: es JavaScript vanilla. Para probar cambios, recarga la extensión desde la página de extensiones del navegador y actualiza la pestaña de YouTube.

### Licencia

Consulta el archivo [LICENSE](LICENSE). Este proyecto es un fork; la licencia distingue entre las aportaciones propias y el código heredado del proyecto original.

---

## English

### Table of contents

- [Overview](#overview)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Configuration](#configuration)
- [Privacy](#privacy)
- [Project structure](#project-structure)
- [Development](#development)
- [License](#license)

### Overview

A browser extension that **detects and automatically skips sponsored segments** in YouTube videos. It uses the video transcript and a [Groq](https://groq.com/) language model to locate advertising mentions and offers a button to skip them.

Compatible with **Chrome, Edge and Firefox** through Manifest V3.

### Features

- **Smart sponsor detection** using Groq's `llama-3.3-70b-versatile` model.
- **"Skip Sponsor" button** overlaid on the player when a sponsorship is detected.
- **Confirmation panel** to review the segment before skipping.
- **Transcript panel** with the analyzed fragments.
- **Timestamp validation** to prevent incorrect skips.
- **Local configuration**: the API key is stored only in browser storage.
- **Chrome and Firefox support** from the same codebase.

### Requirements

- A [Groq](https://console.groq.com/) account and an **API key** starting with `gsk_`.
- Chrome/Edge 109+ or Firefox 109+.

### Installation

#### Chrome / Edge

1. Download or clone this repository.
2. Open `chrome://extensions/` (or `edge://extensions/`).
3. Enable **Developer mode**.
4. Click **Load unpacked** and select the project folder.
5. Open YouTube and click the extension icon to configure your API key.

#### Firefox

1. Open `about:debugging#/runtime/this-firefox`.
2. Click **Load Temporary Add-on**.
3. Select the `manifest.json` file.

### Configuration

1. Click the **YT Sponsor Skip** icon in the browser toolbar.
2. Enter your **Groq API Key** (`gsk_...`).
3. Click **Save** or **Test connection**.
4. Open any YouTube video: the extension will analyze the transcript and show the skip button whenever it finds a sponsorship.

### Privacy

- The **video transcript is sent to the Groq API** for analysis. It is not sent to any server owned by this project.
- The API key is stored locally in `browser.storage.local` and is never shared with third parties.
- The extension does not collect analytics or telemetry.

### Project structure

```text
yt-sponsor-skip/
├── manifest.json     Extension configuration (Manifest V3)
├── background.js     Service Worker: Groq calls and validation
├── content.js        Logic injected into YouTube: DOM, transcript and skipping
├── content.css       Styles for the button and panels on YouTube
├── popup.html        Configuration UI
├── popup.css
├── popup.js
└── icons/            Extension icons
```

### Development

No build step or dependencies are required: it is vanilla JavaScript. To test changes, reload the extension from the browser's extensions page and refresh the YouTube tab.

### License

See the [LICENSE](LICENSE) file. This project is a fork; the license distinguishes between the author's own contributions and the code inherited from the original project.
