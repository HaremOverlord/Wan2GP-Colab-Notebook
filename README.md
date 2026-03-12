# WanGP Colab Notebook

Google Colab notebook for [WanGP](https://github.com/deepbeepmeep/Wan2GP) - AI Video Generator with CivitAI LoRA support.

## Features

- **All current models**: Wan 2.1/2.2, LTX-2/2.3, Hunyuan Video 1.5, Flux, Qwen, and more
- **CivitAI LoRA integration**: Search, download, and use LoRAs from CivitAI directly
- **Built-in CivitAI browser**: WanGP includes a CivitAI browser plugin in the UI
- **Google Drive support**: Persistent storage for models, LoRAs, and output
- **Full Gradio UI**: Complete WanGP web interface accessible via public URL

## Quick Start

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HaremOverlord/Wan2GP-Colab-Notebook/blob/main/Wan2GP_Complete_UI.ipynb)

1. Click the badge above to open in Google Colab
2. Select GPU runtime (Runtime -> Change runtime type -> GPU)
3. Run all cells sequentially
4. Open the Gradio URL from the output

## CivitAI LoRA Support

The notebook includes functions to search and download LoRAs from CivitAI:

```python
# Search for LoRAs
search_civitai_loras('wan anime')

# Download by version ID
download_civitai_lora(123456, target_model='wan')

# Download by URL
download_civitai_lora_by_url('https://civitai.com/models/...', target_model='wan')
```

### Supported LoRA directories

| Model | Directory |
|-------|-----------|
| Wan 2.1/2.2 (14B) | `loras/wan/` |
| Wan 5B | `loras/wan_5B/` |
| Wan Image-to-Video | `loras/wan_i2v/` |
| Hunyuan Video | `loras/hunyuan/` |
| LTX Video / LTX-2 | `loras/ltxv/` |
| Flux | `loras/flux/` |
| Qwen | `loras/qwen/` |

## GPU Requirements

| GPU | VRAM | Recommended Models |
|-----|------|--------------------|
| T4 | 15 GB | LTX-2 Distilled FP8, Wan 5B (480p) |
| L4/A10 | 24 GB | LTX-2 Distilled, Wan 14B (720p) |
| A100 | 40+ GB | LTX-2 Dev 19B, Wan 14B (1080p) |

## Links

- [WanGP Repository](https://github.com/deepbeepmeep/Wan2GP)
- [WanGP LoRA Documentation](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md)
- [WanGP Changelog](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)
- [CivitAI](https://civitai.com)

## License

This project follows the license of the original WanGP project.

## Credits

- **WanGP**: [deepbeepmeep](https://github.com/deepbeepmeep)
- **Colab Notebook**: HaremOverlord
