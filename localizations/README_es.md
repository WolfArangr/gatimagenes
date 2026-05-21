# Localización al Español de Gatimagenes

## Descripción

Este archivo contiene la localización completa al español de España para la interfaz de usuario de Gatimagenes, un generador de imágenes con IA.

## Archivos de Localización

### `es.json`
Archivo JSON principal que contiene todos los strings de la interfaz de usuario en español. Incluye:

- **Nombres de pestañas**: txt2img, img2img, Extras, Configuración, etc.
- **Parámetros de generación**: Indicación, Alto, Ancho, Escala CFG, etc.
- **Botones**: Generar, Interrumpir, Saltar, Guardar, etc.
- **Tooltips**: Textos de ayuda para cada elemento
- **Estilos**: Gestión de estilos de indicaciones
- **Entrenamiento**: Inserción de texturas e hiperrredes
- **Extras**: Herramientas de postprocesamiento
- **Configuración**: Opciones de la interfaz de usuario

### `es_spain_ui.py`
Archivo Python que mapea IDs de elementos HTML a sus traducciones al español. Útil para modificar elementos específicos de la interfaz si es necesario.

## Instalación

1. Coloca el archivo `es.json` en el directorio `localizations/`:
   ```
   localizations/es.json
   ```

2. Reinicia la aplicación para que se cargue la localización.

## Uso

### En la Interfaz de Usuario

1. Abre la aplicación
2. Ve a la pestaña **Configuración**
3. Busca la opción **Localización**
4. Selecciona **Español (España)** o **es** en el menú desplegable
5. La interfaz se actualizará inmediatamente

### Para Desarrolladores

Si necesitas agregar nuevas traducciones:

1. Abre `es.json`
2. Busca la clave que deseas traducir
3. Agrega la traducción española
4. Guarda el archivo
5. Recarga la página para ver los cambios

## Estructura de Traducción

El archivo `es.json` utiliza un formato de pares clave-valor:

```json
{
  "clave": "Traducción al español",
  "prompt": "Indicación",
  "generate": "Generar",
  "generate_button": "Generar"
}
```

## Cobertura de Traducción

Esta localización cubre:

- ✅ Interfaz principal (txt2img, img2img, Extras)
- ✅ Parámetros de generación
- ✅ Botones y herramientas
- ✅ Estilos de indicaciones
- ✅ Entrenamiento (Inserción y Hiperrredes)
- ✅ Configuración
- ✅ Tooltips de ayuda
- ✅ Mensajes de error y éxito
- ✅ Nombres de campos

## Notas de Traducción

- Se utiliza español de España (voseo, vocabulario ibérico)
- Se mantienen algunos términos técnicos en inglés si son más comúnmente usados
- Los tooltips incluyen explicaciones en español
- Se respeta la estructura original de la interfaz

## Contribuciones

Si encuentras errores de traducción o deseas mejorar la localización:

1. Fork el repositorio
2. Realiza tus cambios
3. Envía un pull request

## Términos Técnicos Traducidos

- **Prompt/Indicación**: La descripción de lo que quieres generar
- **Sampler/Muestreador**: Método de muestreo usado en la generación
- **CFG Scale/Escala CFG**: Parámetro de orientación de la indicación
- **Batch/Lote**: Cantidad de imágenes a generar
- **Embedding/Inserción**: Técnica de entrenamiento de texturas
- **Hypernetwork/Hiperred**: Red neuronal para estilo personalizado
- **LoRA**: Adaptación de rango bajo
- **Inpaint/Pintura**: Edición de zonas específicas
- **Upscale/Ampliación**: Aumentar la resolución
- **Denoise/Desnoise**: Reducir artefactos y ruido

## Licencia

Esta localización se proporciona bajo la misma licencia que Gatimagenes (GNU Affero General Public License v3.0).
