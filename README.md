# stable-diffusion-configurator
A utility for automatically downloading stable diffusion model weights from civit.ai and the web

## Install

To install the utility, run the following commands:
```bash
wget https://raw.githubusercontent.com/SaladTechnologies/stable-diffusion-configurator/main/configure
chmod +x configure
```

## Use

To use the utility, specify the models and the output paths for the models you want to download.
This can be done with environment variables or command line arguments, or a mix.
If both are present, the command line arguments take precedence.
The utility will download the models from civit.ai and the web and save them to the specified paths.
The utility will also download the extensions from the specified git urls and save them to the specified paths.
The utility logs a JSON manifest of the downloaded models and extensions to the console.

```
Usage: ./configure [--options] [--help]
  --ckpt-path <path>: path where checkpoints should be saved. Env: CKPT_PATH
  --vae-path <path>: path where vae weights should be saved. Env: VAE_PATH
  --controlnet-model-path <path>: path where controlnet models should be saved. Env: CONTROLNET_MODEL_PATH
  --lora-path <path>: path where lora models should be saved. Env: LORA_PATH
  --extension-path <path>: path where extensions should be saved. Env: EXTENSION_PATH
  --civitai-version-ids <ids>: comma separated list of civitai version ids. Env: CIVITAI_MODEL_VERSION_IDS
  --ckpt-urls <urls>: comma separated list of urls to download checkpoints from. Env: CKPT_URLS
  --vae-urls <urls>: comma separated list of urls to download vae weights from. Env: VAE_URLS
  --controlnet-model-urls <urls>: comma separated list of urls to download controlnet models from. Env: CONTROLNET_URLS
  --lora-urls <urls>: comma separated list of urls to download lora models from. Env: LORA_URLS
  --extension-urls <urls>: comma separated list of git urls to download extensions from. Env: EXTENSION_URLS
  --sdxl-base: download SDXL base model. 1 for yes, 0 for no. Default is 0. Env: LOAD_SDXL_BASE
  --sdxl-refiner: download SDXL refiner model. 1 for yes, 0 for no. Default is 0. Env: LOAD_REFINER
  --help: print this message
```

### Example, capturing the manifest

```bash
manifest=$(./configure --ckpt-path ./data/models/ckpt --civitai-version-ids 128713)
echo $manifest
# { "models": { "checkpoints": [ "dreamshaper_8.safetensors" ], "vae": [], "controlnet": [], "lora": [] }, "extensions": [], "sdxl": false }
```