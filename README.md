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
The utility will download the models from civit.ai and the web and save them to the specified paths.
The utility will also download the extensions from the specified git urls and save them to the specified paths.
The utility logs a JSON manifest of the downloaded models and extensions to the console.

```
Usage: ./configure [--options] [--help]
  --ckpt-path <path>: path where checkpoints should be saved
  --vae-path <path>: path where vae weights should be saved
  --controlnet-model-path <path>: path where controlnet models should be saved
  --lora-path <path>: path where lora models should be saved
  --extension-path <path>: path where extensions should be saved
  --civitai-version-ids <ids>: comma separated list of civitai version ids
  --ckpt-urls <urls>: comma separated list of urls to download checkpoints from
  --vae-urls <urls>: comma separated list of urls to download vae weights from
  --controlnet-model-urls <urls>: comma separated list of urls to download controlnet models from
  --lora-urls <urls>: comma separated list of urls to download lora models from
  --extension-urls <urls>: comma separated list of git urls to download extensions from
  --sdxl-base: download SDXL base model. 1 for yes, 0 for no. Default is 0.
  --sdxl-refiner: download SDXL refiner model. 1 for yes, 0 for no. Default is 0.
  --help: print this message
```

### Example, capturing the manifest

```bash
manifest=$(./configure --ckpt-path ./data/models/ckpt --civitai-version-ids 128713)
echo $manifest
# { "models": { "checkpoints": [ "dreamshaper_8.safetensors" ], "vae": [], "controlnet": [], "lora": [] }, "extensions": [], "sdxl": false }
```