Interfaz web de Stable Diffusion
Una interfaz web para Stable Diffusion, implementada con la biblioteca Gradio.



Funcionalidades
Demostración detallada de funciones con imágenes:

Modos originales de txt2img e img2img

Script de instalación y ejecución con un solo clic (aun así, necesitas tener Python y Git instalados)

Outpainting (ampliación de imágenes)

Inpainting (relleno o modificación de zonas de una imagen)

Boceto a color

Matriz de prompts

Escalado de imágenes con Stable Diffusion

Atención en el prompt: permite indicar al modelo qué partes del texto deben recibir más atención

Ejemplo: un hombre con un ((smoking)) — prestará más atención al smoking

Alternativa: un hombre con un (smoking:1.21)

Selecciona texto y pulsa Ctrl+Arriba o Ctrl+Abajo (o Command+Arriba/Abajo en MacOS) para ajustar automáticamente el nivel de atención (código aportado por un usuario anónimo)

Loopback: permite aplicar img2img varias veces sobre la misma imagen

Gráfica X/Y/Z: genera una gráfica tridimensional con imágenes según distintos parámetros

Textual Inversion:

Usa tantos embeddings como quieras y nómbralos como prefieras

Compatible con múltiples embeddings con diferente número de vectores por token

Compatible con precisión de coma flotante de 16 bits

Entrenamiento posible en GPUs de 8GB (también se han reportado casos exitosos con 6GB)

Pestaña “Extras” con:

GFPGAN: red neuronal para restauración facial

CodeFormer: alternativa a GFPGAN para restauración de rostros

RealESRGAN: red neuronal para escalado

ESRGAN: otra red neuronal de escalado con muchos modelos de terceros

SwinIR y Swin2SR (ver aquí)

LDSR: superresolución por difusión latente

Opciones de relación de aspecto al redimensionar

Selección del método de muestreo

Ajuste del parámetro eta del muestreador (multiplicador de ruido)

Opciones avanzadas de configuración de ruido

Posibilidad de interrumpir el proceso en cualquier momento

Soporte para tarjetas gráficas de 4GB (también se ha probado con 2GB)

Semillas correctas para lotes

Validación en tiempo real de la longitud del prompt

Parámetros de generación:

Se guardan junto con la imagen

En fragmentos PNG para PNG, en EXIF para JPEG

Arrastrar la imagen a la pestaña “PNG Info” para restaurar los parámetros automáticamente

Se puede desactivar en configuración

También puedes arrastrar y soltar una imagen o parámetros de texto al campo del prompt

Botón "Leer parámetros de generación", para cargar automáticamente los parámetros en la interfaz

Página de configuración

Posibilidad de ejecutar código Python arbitrario desde la interfaz (requiere ejecutarse con --allow-code)

Información emergente al pasar el ratón sobre elementos de la interfaz

Personalización de valores por defecto/mínimo/máximo/paso de los controles mediante archivo de texto

Soporte para creación de imágenes en mosaico (tileables)

Barra de progreso y previsualización en tiempo real

Puede usarse una red neuronal separada para previsualizaciones sin apenas usar VRAM o cómputo

Prompt negativo: campo adicional para indicar lo que no quieres que aparezca en la imagen

Estilos: guarda partes de un prompt para aplicarlos fácilmente desde un desplegable

Variaciones: genera versiones ligeramente diferentes de una misma imagen

Redimensionado por semilla: genera la misma imagen a resoluciones ligeramente distintas

Interrogador CLIP: botón que intenta adivinar el prompt de una imagen

Edición del prompt durante la generación: cambia el prompt a mitad del proceso (ej. de sandía a chica anime)

Procesamiento por lotes: procesa un grupo de archivos con img2img

Alternativa img2img: método inverso de Euler para control de atención cruzada

Corrección de alta resolución (Highres Fix): mejora imágenes en alta resolución con un solo clic

Recarga de checkpoints en caliente

Fusionador de modelos: permite combinar hasta 3 checkpoints en uno

Scripts personalizados con muchas extensiones creadas por la comunidad

Composable-Diffusion: uso de múltiples prompts a la vez

Separa los prompts con AND en mayúsculas

Admite pesos: un gato :1.2 AND un perro AND un pingüino :2.2

Sin límite de tokens para prompts (el modelo original permite hasta 75)

Integración con DeepDanbooru: genera etiquetas al estilo Danbooru para prompts de anime

xformers: gran mejora de velocidad en ciertas tarjetas (añade --xformers en los argumentos de ejecución)

Mediante extensión: Pestaña de historial: visualiza, organiza y elimina imágenes desde la interfaz

Opción de generar infinitamente

Pestaña de entrenamiento:

Opciones para hypernetworks y embeddings

Preprocesamiento de imágenes: recorte, reflejo, autoetiquetado (con BLIP o DeepDanbooru para anime)

Clip skip

Hypernetworks

Loras (como hypernetworks pero más refinados)

Interfaz específica para seleccionar con vista previa qué embeddings, hypernetworks o Loras añadir al prompt

Selección de VAE desde la configuración

Estimación del tiempo restante en la barra de progreso

API

Soporte para modelos específicos de inpainting de RunwayML

Mediante extensión: Gradientes estéticos, genera imágenes con una estética concreta usando embeddings de imágenes clip (implementación)

Compatibilidad con Stable Diffusion 2.0 – consulta la wiki

Soporte para Alt-Diffusion – ver wiki

¡Sin letras raras!

Soporte para checkpoints en formato safetensors

Restricción de resolución más flexible: las dimensiones deben ser múltiplos de 8 (en lugar de 64)

¡Ahora con licencia!

Reordenar elementos de la interfaz desde la pantalla de configuración

Compatibilidad con Segmind Stable Diffusion

## Installation and Running
Make sure the required [dependencies](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Dependencies) are met and follow the instructions available for:
- [NVidia](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs) (recommended)
- [AMD](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-AMD-GPUs) GPUs.
- [Intel CPUs, Intel GPUs (both integrated and discrete)](https://github.com/openvinotoolkit/stable-diffusion-webui/wiki/Installation-on-Intel-Silicon) (external wiki page)
- [Ascend NPUs](https://github.com/wangshuai09/stable-diffusion-webui/wiki/Install-and-run-on-Ascend-NPUs) (external wiki page)

Alternatively, use online services (like Google Colab):

- [List of Online Services](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Online-Services)

### Installation on Windows 10/11 with NVidia-GPUs using release package
1. Download `sd.webui.zip` from [v1.0.0-pre](https://github.com/AUTOMATIC1111/stable-diffusion-webui/releases/tag/v1.0.0-pre) and extract its contents.
2. Run `update.bat`.
3. Run `run.bat`.
> For more details see [Install-and-Run-on-NVidia-GPUs](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Install-and-Run-on-NVidia-GPUs)

### Automatic Installation on Windows
1. Install [Python 3.10.6](https://www.python.org/downloads/release/python-3106/) (Newer version of Python does not support torch), checking "Add Python to PATH".
2. Install [git](https://git-scm.com/download/win).
3. Download the stable-diffusion-webui repository, for example by running `git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git`.
4. Run `webui-user.bat` from Windows Explorer as normal, non-administrator, user.

### Automatic Installation on Linux
1. Install the dependencies:
```bash
# Debian-based:
sudo apt install wget git python3 python3-venv libgl1 libglib2.0-0
# Red Hat-based:
sudo dnf install wget git python3 gperftools-libs libglvnd-glx
# openSUSE-based:
sudo zypper install wget git python3 libtcmalloc4 libglvnd
# Arch-based:
sudo pacman -S wget git python3
```
If your system is very new, you need to install python3.11 or python3.10:
```bash
# Ubuntu 24.04
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt update
sudo apt install python3.11

# Manjaro/Arch
sudo pacman -S yay
yay -S python311 # do not confuse with python3.11 package

# Only for 3.11
# Then set up env variable in launch script
export python_cmd="python3.11"
# or in webui-user.sh
python_cmd="python3.11"
```
2. Navigate to the directory you would like the webui to be installed and execute the following command:
```bash
wget -q https://raw.githubusercontent.com/AUTOMATIC1111/stable-diffusion-webui/master/webui.sh
```
Or just clone the repo wherever you want:
```bash
git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui
```

3. Run `webui.sh`.
4. Check `webui-user.sh` for options.
### Installation on Apple Silicon

Find the instructions [here](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Installation-on-Apple-Silicon).

## Contributing
Here's how to add code to this repo: [Contributing](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Contributing)

## Documentation

The documentation was moved from this README over to the project's [wiki](https://github.com/AUTOMATIC1111/stable-diffusion-webui/wiki).

For the purposes of getting Google and other search engines to crawl the wiki, here's a link to the (not for humans) [crawlable wiki](https://github-wiki-see.page/m/AUTOMATIC1111/stable-diffusion-webui/wiki).

## Credits
Licenses for borrowed code can be found in `Settings -> Licenses` screen, and also in `html/licenses.html` file.

- Stable Diffusion - https://github.com/Stability-AI/stablediffusion, https://github.com/CompVis/taming-transformers, https://github.com/mcmonkey4eva/sd3-ref
- k-diffusion - https://github.com/crowsonkb/k-diffusion.git
- Spandrel - https://github.com/chaiNNer-org/spandrel implementing
  - GFPGAN - https://github.com/TencentARC/GFPGAN.git
  - CodeFormer - https://github.com/sczhou/CodeFormer
  - ESRGAN - https://github.com/xinntao/ESRGAN
  - SwinIR - https://github.com/JingyunLiang/SwinIR
  - Swin2SR - https://github.com/mv-lab/swin2sr
- LDSR - https://github.com/Hafiidz/latent-diffusion
- MiDaS - https://github.com/isl-org/MiDaS
- Ideas for optimizations - https://github.com/basujindal/stable-diffusion
- Cross Attention layer optimization - Doggettx - https://github.com/Doggettx/stable-diffusion, original idea for prompt editing.
- Cross Attention layer optimization - InvokeAI, lstein - https://github.com/invoke-ai/InvokeAI (originally http://github.com/lstein/stable-diffusion)
- Sub-quadratic Cross Attention layer optimization - Alex Birch (https://github.com/Birch-san/diffusers/pull/1), Amin Rezaei (https://github.com/AminRezaei0x443/memory-efficient-attention)
- Textual Inversion - Rinon Gal - https://github.com/rinongal/textual_inversion (we're not using his code, but we are using his ideas).
- Idea for SD upscale - https://github.com/jquesnelle/txt2imghd
- Noise generation for outpainting mk2 - https://github.com/parlance-zz/g-diffuser-bot
- CLIP interrogator idea and borrowing some code - https://github.com/pharmapsychotic/clip-interrogator
- Idea for Composable Diffusion - https://github.com/energy-based-model/Compositional-Visual-Generation-with-Composable-Diffusion-Models-PyTorch
- xformers - https://github.com/facebookresearch/xformers
- DeepDanbooru - interrogator for anime diffusers https://github.com/KichangKim/DeepDanbooru
- Sampling in float32 precision from a float16 UNet - marunine for the idea, Birch-san for the example Diffusers implementation (https://github.com/Birch-san/diffusers-play/tree/92feee6)
- Instruct pix2pix - Tim Brooks (star), Aleksander Holynski (star), Alexei A. Efros (no star) - https://github.com/timothybrooks/instruct-pix2pix
- Security advice - RyotaK
- UniPC sampler - Wenliang Zhao - https://github.com/wl-zhao/UniPC
- TAESD - Ollin Boer Bohan - https://github.com/madebyollin/taesd
- LyCORIS - KohakuBlueleaf
- Restart sampling - lambertae - https://github.com/Newbeeer/diffusion_restart_sampling
- Hypertile - tfernd - https://github.com/tfernd/HyperTile
- Initial Gradio script - posted on 4chan by an Anonymous user. Thank you Anonymous user.
- (You)
