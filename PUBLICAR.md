# Cómo publicar en Descargas

Notas para BOSG. Este repositorio solo guarda el catálogo (`README.md`) y los íconos; los instaladores van en
**Releases**, porque GitHub no acepta archivos de más de 100 MB dentro del repositorio.

## Reglas

- **Una etiqueta por app y versión:** `<app>-v<versión>`, por ejemplo `grayskull-garage-v1.0.0` o `mi-juego-v0.3.0`.
  El nombre de la app va en minúsculas y con guiones.
- **Título del release:** `<Nombre de la app> <versión>`, por ejemplo `Grayskull Garage 1.0.0`.
- **Nombre de los archivos:** `<App>-<versión>-<sistema>…`, por ejemplo `Mi-Juego-0.3.0-android.apk`.
- **Íconos:** en `iconos/<app>.png` (192 × 192 está bien).

## Agregar una app nueva

1. Sube su ícono a `iconos/`.
2. En `README.md`, agrega una fila en la tabla **Apps** y una sección nueva copiando la de Grayskull Garage
   (descripción, funciones y tabla de descargas).
3. Encierra la tabla de descargas entre estos marcadores, para que una publicación automática pueda reemplazarla:

   ```
   <!-- descargas:<app>:inicio -->
   | Sistema | Descarga | Versión |
   |---|---|---|
   | 🤖 Android | [Mi-Juego-0.3.0-android.apk](https://github.com/bosc12/Descargas/releases/download/mi-juego-v0.3.0/Mi-Juego-0.3.0-android.apk) | 0.3.0 |
   <!-- descargas:<app>:fin -->
   ```

4. Crea el release con su etiqueta y adjunta los archivos (desde la web de GitHub o con
   `gh release create mi-juego-v0.3.0 -R bosc12/Descargas --title "Mi Juego 0.3.0" archivo.apk`).

## Publicación automática desde otro repositorio

Grayskull Garage publica solo: su flujo de GitHub Actions construye los instaladores, crea el release aquí y actualiza
su tabla de descargas. Usa el secreto **`JUEGOSAPPS`**, un token con permiso de escritura (*Contents: Read and write*)
sobre este repositorio. Para otra app, agrega ese mismo secreto en su repositorio y copia el trabajo `publicar` de
`grayskull-garage/.github/workflows/release.yml`.
