# Validador de Hojas de Ruta

Página estática de una sola pantalla que compara la plantilla de importación de una hoja de ruta SAP contra el export de SAP post-modificación, y confirma qué cambios se aplicaron correctamente.

- Sube el archivo "antes" (plantilla con los cambios a importar) y el "después" (export de SAP).
- Empareja las filas por **Grupo hojas ruta + Cont.grupo HRuta + Centro + Operación** (configurable en pantalla).
- Compara todas las columnas y clasifica cada fila como Correcta, Modificada, No efectuada en SAP, o Nueva/inesperada.
- Todo el procesamiento ocurre en el navegador del usuario: los archivos .xlsx nunca se suben a un servidor. El parseo de `.xlsx` está implementado desde cero (ZIP + XML) usando únicamente APIs nativas del navegador (`DecompressionStream`, `DOMParser`), sin dependencias externas.

## Despliegue

Sitio 100% estático (`index.html`). En Vercel: **Add New → Project → Import** este repositorio, sin build command ni framework — Vercel lo sirve tal cual.

## Requisitos del navegador

Necesita un navegador con soporte para `DecompressionStream` (Chrome/Edge/Firefox/Safari recientes, ~2023+).
