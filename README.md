# Text-to-Image Generator (Pretrained Stable Diffusion)       

A web app that generates images from text prompts using a **pretrained** diffusion model — no training required. Built with Hugging Face `diffusers` and a `Gradio` UI, designed to run for free on Google Colab.

## How it works

1. **Pretrained model**: `runwayml/stable-diffusion-v1-5`, loaded directly from Hugging Face Hub via the `diffusers` library.
2. **Pipeline**: `StableDiffusionPipeline` handles text encoding (CLIP), the diffusion denoising loop (U-Net), and image decoding (VAE) internally.
3. **UI**: Gradio wraps the generation function in a browser-based interface with prompt input, negative prompt, and tunable parameters (inference steps, guidance scale, resolution, seed).
4. **Deployment**: `demo.launch(share=True)` gives you a public shareable link directly from Colab.

## Run it

1. Open `Image_Generation_App.ipynb` in Google Colab.
2. `Runtime > Change runtime type > T4 GPU`.
3. Run all cells (`Runtime > Run all`).
4. Open the public Gradio link printed at the bottom of the last cell.

First run downloads the model (~4 GB), so expect a few minutes on the first cell that loads the pipeline. Subsequent generations take roughly 10-20 seconds on a T4 GPU.

## Parameters explained

| Parameter | What it does |
|---|---|
| Prompt | Text description of the image you want |
| Negative prompt | Things to steer the model away from (e.g. "blurry, low quality") |
| Inference steps | Number of denoising steps; higher = more detail but slower (20-40 is a good range) |
| Guidance scale | How strictly the model follows your prompt vs. its own creativity (7-8 is typical) |
| Width / Height | Output image dimensions (must be multiples of 8) |
| Seed | Fixes randomness so you can reproduce the same image; -1 picks a random seed each time |

## Project write-up talking points (for your resume/portfolio)

- Built an end-to-end generative AI application using a pretrained diffusion model (Stable Diffusion) via Hugging Face `diffusers`.
- Implemented a configurable inference pipeline (guidance scale, step count, negative prompting, seeded reproducibility).
- Designed and deployed an interactive Gradio web interface for real-time text-to-image generation.
- Optimized for constrained compute (float16 precision, attention slicing) to run on free-tier Colab GPUs.

## Extending the project

- Swap in `stabilityai/sdxl-turbo` for near-instant generation, or a style-specific fine-tuned checkpoint from the Hub.
- Add `StableDiffusionImg2ImgPipeline` for sketch-to-image or style-transfer features.
- Add `stabilityai/stable-diffusion-x4-upscaler` to upscale outputs.
- Deploy permanently on Hugging Face Spaces (free hosting) instead of a temporary Colab link, for a persistent portfolio link.
