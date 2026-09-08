# Zento Sound

Letras sincronizadas con lo que suena en tu Spotify. Web pura, sin servidor:
todo ocurre en el navegador.

- **Qué suena** — API de Spotify, OAuth con PKCE (sin secreto que esconder).
- **Las letras** — LRCLIB, gratis y sin clave.
- **La sincronía** — se consulta a Spotify cada 3 s y entre consultas se
  interpola con `performance.now()`, asi va fluido sin castigar la API.

## La regla de emparejamiento

Probada contra 262 canciones reales: **93.1%** de acierto.

1. Match exacto: artista + titulo + album + duracion
2. Titulo limpio (sin `(feat. …)` ni `- … Remix`) + artista
3. Solo titulo

Los tres pasan por el mismo portero: **duracion ±4 s Y coincidencia de
artista**. Sin el filtro de artista aparecen falsos positivos graves — la
letra de otra cancion con el mismo titulo.

## Puesta en marcha

1. Crear una app en `developer.spotify.com/dashboard`
2. Redirect URI: la URL donde este publicada esta pagina
3. Marcar **Web API**, copiar el **Client ID**
4. Abrir la pagina y pegarlo. Se guarda en el navegador, no viaja a ningun lado.

## En el coche

Pensada para una pantalla Android con navegador. El telefono reproduce por
Bluetooth; la pantalla solo mira la misma cuenta de Spotify y escribe.

Boton de pantalla completa abajo a la derecha, y usa Wake Lock para que la
pantalla no se apague.
