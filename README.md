# Interfaz web de Stable Diffusion

Una interfaz web para Stable Diffusion, implementada con la biblioteca Gradio.

![](screenshot.png)

## Funcionalidades

[Demostración detallada de características con imágenes](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features):

* Modos originales txt2img e img2img
* Script de instalación y ejecución en un solo clic (pero aún debes instalar Python y Git)
* Outpainting
* Inpainting
* Boceto de color
* Matriz de prompts
* Escalado de Stable Diffusion
* Atención: especifica partes del texto a las que el modelo debe prestar más atención

  * un hombre con un `((smoking))` – prestará más atención al esmoquin
  * un hombre con un `(smoking:1.21)` – sintaxis alternativa
  * selecciona el texto y pulsa `Ctrl+Arriba` o `Ctrl+Abajo` (o `Command+Arriba` o `Command+Abajo` si usas MacOS) para ajustar automáticamente la atención al texto seleccionado (código aportado por un usuario anónimo)
* Loopback, ejecuta el procesamiento img2img varias veces
* Gráfico X/Y/Z, una forma de trazar un gráfico tridimensional de imágenes con distintos parámetros
* Inversión textual

  * puedes tener tantas incrustaciones como quieras y usar cualquier nombre para ellas
  * usa múltiples incrustaciones con diferente número de vectores por token
  * funciona con números de coma flotante de media precisión
  * entrena incrustaciones con 8 GB (también se han reportado casos con 6 GB)
* Pestaña de extras con:

  * GFPGAN, red neuronal que corrige caras
  * CodeFormer, herramienta de restauración facial alternativa a GFPGAN
  * RealESRGAN, escalador con red neuronal
  * ESRGAN, escalador con red neuronal con muchos modelos de terceros
  * SwinIR y Swin2SR ([ver aquí](https://github.com/AUTOMATIC1111/stable-diffusion-webui/pull/2092)), escaladores con redes neuronales
  * LDSR, escalado de superresolución por difusión latente
* Opciones de redimensionamiento de relación de aspecto
* Selección de método de muestreo

  * Ajuste de valores eta del muestreador (multiplicador de ruido)
  * Más opciones avanzadas de configuración de ruido
* Interrumpir el procesamiento en cualquier momento
* Soporte para tarjetas gráficas de 4 GB (también hay reportes de 2 GB funcionando)
* Semillas correctas para lotes
* Validación en directo de la longitud del prompt en tokens
* Parámetros de generación

  * los parámetros usados para generar imágenes se guardan con la imagen
  * en bloques PNG para PNG, en EXIF para JPEG
  * puedes arrastrar la imagen a la pestaña de información PNG para restaurar los parámetros de generación y copiarlos automáticamente en la interfaz
  * se puede desactivar en los ajustes
  * arrastra y suelta una imagen o parámetros en texto en el cuadro de prompt
* Botón Leer parámetros de generación, carga los parámetros al cuadro de prompt en la interfaz
* Página de configuración
* Ejecución de código Python arbitrario desde la interfaz (debe ejecutarse con `--allow-code` para habilitarlo)
* Pistas emergentes al pasar el ratón por encima de la mayoría de los elementos de la interfaz
* Posibilidad de cambiar valores predeterminados/mínimos/máximos/pasos para los elementos de la interfaz mediante archivo de configuración de texto
* Soporte de teselado, una casilla para crear imágenes que se puedan repetir como texturas
* Barra de progreso y vista previa de generación de imagen en tiempo real

  * Se puede usar una red neuronal separada para generar vistas previas sin apenas necesidad de VRAM ni cómputo
* Prompt negativo, un campo de texto adicional para indicar lo que no quieres que aparezca en la imagen generada
* Estilos, una forma de guardar partes del prompt y aplicarlos fácilmente desde un desplegable
* Variaciones, una forma de generar la misma imagen con pequeñas diferencias
* Redimensionamiento de semilla, una forma de generar la misma imagen con una resolución ligeramente distinta
* Interrogador CLIP, un botón que intenta adivinar el prompt a partir de una imagen
* Edición de prompt, una forma de cambiar el prompt durante la generación, por ejemplo para empezar generando una sandía y cambiar a chica anime a mitad
* Procesamiento por lotes, procesa un grupo de archivos usando img2img
* Alternativa a img2img, método Euler inverso para el control de atención cruzada
* Corrección de alta resolución, opción para generar imágenes en alta resolución con un clic sin distorsiones habituales
* Recarga de checkpoints al vuelo
* Combinador de checkpoints, una pestaña que permite fusionar hasta 3 checkpoints en uno
* [Scripts personalizados](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Custom-Scripts) con muchas extensiones de la comunidad
* [Composable-Diffusion](https://energy-based-model.github.io/Compositional-Visual-Generation-with-Composable-Diffusion-Models/), una forma de usar múltiples prompts a la vez

  * separa prompts usando `AND` en mayúsculas
  * también admite pesos para prompts: `a cat :1.2 AND a dog AND a penguin :2.2`
* Sin límite de tokens para prompts (Stable Diffusion original permite hasta 75 tokens)
* Integración de DeepDanbooru, genera etiquetas estilo Danbooru para prompts anime
* [xformers](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Xformers), mejora de velocidad significativa en ciertas tarjetas: (añade `--xformers` a los argumentos de línea de comandos)
* mediante extensión: [Pestaña de historial](https://github.com/yfszzx/stable-diffusion-webui-images-browser): ver, dirigir y borrar imágenes cómodamente desde la interfaz
* Opción de generar indefinidamente
* Pestaña de entrenamiento

  * opciones de hiperrredes e incrustaciones
  * Preprocesado de imágenes: recorte, reflejo, autoetiquetado con BLIP o deepdanbooru (para anime)
* Clip skip
* Hypernetworks
* Loras (como las Hypernetworks pero más bonitas)
* Una interfaz separada donde puedes elegir, con vista previa, qué incrustaciones, hiperrredes o Loras añadir a tu prompt
* Posibilidad de seleccionar un VAE diferente desde la pantalla de ajustes
* Tiempo estimado de finalización en la barra de progreso
* API
* Soporte para [modelo específico de inpainting](https://github.com/runwayml/stable-diffusion#inpainting-with-stable-diffusion) de RunwayML
* mediante extensión: [Aesthetic Gradients](https://github.com/AUTOMATIC1111/stable-diffusion-webui-aesthetic-gradients), una forma de generar imágenes con una estética concreta usando incrustaciones CLIP de imágenes ([implementación](https://github.com/vicgalle/stable-diffusion-aesthetic-gradients))
* Soporte para [Stable Diffusion 2.0](https://github.com/Stability-AI/stablediffusion) – ver [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features#stable-diffusion-20) para instrucciones
* Soporte para [Alt-Diffusion](https://arxiv.org/abs/2211.06679) – ver [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Features#alt-diffusion) para instrucciones
* ¡Ahora sin letras chungas!
* Carga de checkpoints en formato safetensors
* Restricción de resolución suavizada: las dimensiones de la imagen generada deben ser múltiplos de 8 en lugar de 64
* ¡Ahora con licencia!
* Reordenar elementos en la interfaz desde la pantalla de ajustes
* Soporte para [Segmind Stable Diffusion](https://huggingface.co/segmind/SSD-1B)

---

## Instalación y ejecución

Asegúrate de cumplir con las [dependencias](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Dependencies) necesarias y sigue las instrucciones disponibles para:

* [NVidia](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs) (recomendado)
* GPUs [AMD](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs).
* [CPUs Intel, GPUs Intel (integradas y discretas)](https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon) (página externa del wiki)
* [NPUs Ascend](https://github.com/wangshuai09/stable-diffusion-webui/wiki/Install-and-run-on-Ascend-NPUs) (página externa del wiki)

También puedes usar servicios online (como Google Colab):

* [Lista de servicios online](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

### Instalación en Windows 10/11 con GPUs NVidia usando paquete de lanzamiento

1. Descarga `sd.webui.zip` desde [v1.0.0-pre](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.0.0-pre) y extrae su contenido.
2. Ejecuta `update.bat`.
3. Ejecuta `run.bat`.

> Para más detalles, consulta [Install-and-Run-on-NVidia-GPUs](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs)

### Instalación automática en Windows

1. Instala [Python 3.10.6](https://www.python.org/downloads/release/python-3106/) (Versiones más recientes de Python no son compatibles con torch), marcando la opción "Add Python to PATH".
2. Instala [git](https://git-scm.com/download/win).
3. Descarga el repositorio stable-diffusion-webui, por ejemplo ejecutando `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git`.
4. Ejecuta `webui-user.bat` desde el Explorador de archivos de Windows como usuario normal (no administrador).

### Instalación automática en Linux

1. Instala las dependencias:

```bash
# Basado en Debian:
sudo apt install wget git python3 python3-venv libgl1 libglib2.0-0
# Basado en Red Hat:
sudo dnf install wget git python3 gperftools-libs libglvnd-glx
# Basado en openSUSE:
sudo zypper install wget git python3 libtcmalloc4 libglvnd
# Basado en Arch:
sudo pacman -S wget git python3
```

Si tu sistema es muy nuevo, necesitas instalar python3.11 o python3.10:

```bash
# Ubuntu 24.04
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.11

# Manjaro/Arch
sudo pacman -S yay
yay -S python311 # no confundir con el paquete python3.11

# Solo para 3.11
# Luego establece la variable de entorno en el script de lanzamiento
export python_cmd="python3.11"
# o en webui-user.sh
python_cmd="python3.11"
```

2. Navega al directorio donde quieras instalar la interfaz web y ejecuta el siguiente comando:

```bash
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh
```

O simplemente clona el repositorio donde quieras:

```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
```

3. Ejecuta `webui.sh`.
4. Revisa `webui-user.sh` para más opciones.

### Instalación en Apple Silicon

Encuentra las instrucciones [aquí](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon).

## Contribuir

Aquí tienes cómo aportar código a este repositorio: [Contributing](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Contributing)

## Documentación

La documentación se ha trasladado desde este README al [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki) del proyecto.

Con el fin de que Google y otros motores de búsqueda rastreen el wiki, aquí tienes un enlace al [wiki rastreable](https://github-wiki-see.page/m/AUTOMATIC1111/stable-diffusion-webui/wiki) (no pensado para humanos).

## Créditos

Las licencias del código reutilizado pueden encontrarse en la pantalla `Ajustes -> Licencias` y también en el archivo `html/licenses.html`.

* Stable Diffusion - [https://github.com/Stability-AI/stablediffusion](https://github.com/Stability-AI/stablediffusion), [https://github.com/CompVis/taming-transformers](https://github.com/CompVis/taming-transformers), [https://github.com/mcmonkey4eva/sd3-ref](https://github.com/mcmonkey4eva/sd3-ref)
* k-diffusion - [https://github.com/crowsonkb/k-diffusion.git](https://github.com/crowsonkb/k-diffusion.git)
* Spandrel - [https://github.com/chaiNNer-org/spandrel](https://github.com/chaiNNer-org/spandrel) implementando

  * GFPGAN - [https://github.com/TencentARC/GFPGAN.git](https://github.com/TencentARC/GFPGAN.git)
  * CodeFormer - [https://github.com/sczhou/CodeFormer](https://github.com/sczhou/CodeFormer)
  * ESRGAN - [https://github.com/xinntao/ESRGAN](https://github.com/xinntao/ESRGAN)
  * SwinIR - [https://github.com/JingyunLiang/SwinIR](https://github.com/JingyunLiang/SwinIR)
  * Swin2SR - [https://github.com/mv-lab/swin2sr](https://github.com/mv-lab/swin2sr)
* LDSR - [https://github.com/Hafiidz/latent-diffusion](https://github.com/Hafiidz/latent-diffusion)
* MiDaS - [https://github.com/isl-org/MiDaS](https://github.com/isl-org/MiDaS)
* Ideas para optimizaciones - [https://github.com/basujindal/stable-diffusion](https://github.com/basujindal/stable-diffusion)
* Optimización de la capa de Atención Cruzada - Doggettx - [https://github.com/Doggettx/stable-diffusion](https://github.com/Doggettx/stable-diffusion), idea original para edición de prompts.
* Optimización de la capa de Atención Cruzada - InvokeAI, lstein - [https://github.com/invoke-ai/InvokeAI](https://github.com/invoke-ai/InvokeAI) (originalmente [http://github.com/lstein/stable-diffusion](http://github.com/lstein/stable-diffusion))
* Optimización subcuadrática de la capa de Atención Cruzada - Alex Birch ([https://github.com/Birch-san/diffusers/pull/1](https://github.com/Birch-san/diffusers/pull/1)), Amin Rezaei ([https://github.com/AminRezaei0x443/memory-efficient-attention](https://github.com/AminRezaei0x443/memory-efficient-attention))
* Inversión textual - Rinon Gal - [https://github.com/rinongal/textual\_inversion](https://github.com/rinongal/textual_inversion) (no usamos su código, pero sí sus ideas).
* Idea para escalado con SD - [https://github.com/jquesnelle/txt2imghd](https://github.com/jquesnelle/txt2imghd)
* Generación de ruido para outpainting mk2 - [https://github.com/parlance-zz/g-diffuser-bot](https://github.com/parlance-zz/g-diffuser-bot)
* Idea del interrogador CLIP y algo de código reutilizado - [https://github.com/pharmapsychotic/clip-interrogator](https://github.com/pharmapsychotic/clip-interrogator)
* Idea para Composable Diffusion - [https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch](https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch)
* xformers - [https://github.com/facebookresearch/xformers](https://github.com/facebookresearch/xformers)
* DeepDanbooru - interrogador para difusores de anime [https://github.com/KichangKim/DeepDanbooru](https://github.com/KichangKim/DeepDanbooru)
* Muestreo en precisión float32 desde una UNet float16 - idea de marunine, implementación ejemplo de Birch-san ([https://github.com/Birch-san/diffusers-play/tree/92feee6](https://github.com/Birch-san/diffusers-play/tree/92feee6))
* Instruct pix2pix - Tim Brooks (estrella), Aleksander Holynski (estrella), Alexei A. Efros (sin estrella) - [https://github.com/timothybrooks/instruct-pix2pix](https://github.com/timothybrooks/instruct-pix2pix)
* Consejos de seguridad - RyotaK
* Muestreador UniPC - Wenliang Zhao - [https://github.com/wl-zhao/UniPC](https://github.com/wl-zhao/UniPC)
* TAESD - Ollin Boer Bohan - [https://github.com/madebyollin/taesd](https://github.com/madebyollin/taesd)
* LyCORIS - KohakuBlueleaf
* Reinicio del muestreo - lambertae - [https://github.com/Newbeeer/diffusion\_restart\_sampling](https://github.com/Newbeeer/diffusion_restart_sampling)
* Hypertile - tfernd - [https://github.com/tfernd/HyperTile](https://github.com/tfernd/HyperTile)
* Script inicial de Gradio - publicado en 4chan por un usuario anónimo. Gracias, usuario anónimo.
* (Tú)
