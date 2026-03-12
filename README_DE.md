# WanGP Colab Notebook (Deutsch)

Google Colab Notebook fuer [WanGP](https://github.com/deepbeepmeep/Wan2GP) - AI Video Generator mit CivitAI LoRA-Unterstuetzung.

## Features

- **Alle aktuellen Modelle**: Wan 2.1/2.2, LTX-2/2.3, Hunyuan Video 1.5, Flux, Qwen, und mehr
- **CivitAI LoRA-Integration**: LoRAs direkt von CivitAI suchen, herunterladen und verwenden
- **Integrierter CivitAI Browser**: WanGP hat einen eingebauten CivitAI Browser im UI
- **Google Drive**: Persistente Speicherung fuer Modelle, LoRAs und Output
- **Vollstaendiges Gradio UI**: Komplettes WanGP Web-Interface ueber oeffentliche URL

## Schnellstart

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/HaremOverlord/Wan2GP-Colab-Notebook/blob/main/Wan2GP_Complete_UI.ipynb)

1. Klicke auf den Badge oben um das Notebook in Colab zu oeffnen
2. Waehle GPU Runtime (Runtime -> Change runtime type -> GPU)
3. Fuehre alle Zellen der Reihe nach aus
4. Oeffne die Gradio URL aus dem Output

## CivitAI LoRA-Unterstuetzung

Das Notebook enthaelt Funktionen zum Suchen und Herunterladen von LoRAs:

```python
# LoRAs suchen
search_civitai_loras('wan anime')

# Per Version-ID herunterladen
download_civitai_lora(123456, target_model='wan')

# Per URL herunterladen
download_civitai_lora_by_url('https://civitai.com/models/...', target_model='wan')
```

### LoRA-Verzeichnisse

| Modell | Verzeichnis |
|--------|------------|
| Wan 2.1/2.2 (14B) | `loras/wan/` |
| Wan 5B | `loras/wan_5B/` |
| Wan Image-to-Video | `loras/wan_i2v/` |
| Hunyuan Video | `loras/hunyuan/` |
| LTX Video / LTX-2 | `loras/ltxv/` |
| Flux | `loras/flux/` |
| Qwen | `loras/qwen/` |

### LoRAs im UI verwenden

1. **Advanced Tab** -> **Loras** Bereich oeffnen
2. LoRA aus dem Dropdown waehlen
3. Multiplikator setzen (empfohlen: 0.7-1.2)
4. Trigger Words aus der CivitAI-Seite in den Prompt einbauen

### Multiplikator-Syntax

- `1.0` - Einfacher Multiplikator
- `0.9,0.8,0.7` - Zeitbasiert (staerker am Anfang der Generierung)
- `0;1` - Phasenbasiert fuer Wan 2.2 (High Noise Phase; Low Noise Phase)
- `1;0.5` - LTX-2 Multi-Pass (Pass 1; Pass 2)

### Accelerator LoRAs

Spezielle LoRAs die die Generierung beschleunigen:

| LoRA | Steps | Settings |
|------|-------|----------|
| CausVid | 4-12 | Guidance=1, Shift=7 |
| AccVid | Normal | Kein CFG noetig |
| FusioniX | Normal | Guidance=1, Shift=2 |
| Lightx2v 4-steps | 4 | Multiplikator: `1;0 0;1` |

## GPU Empfehlungen

| GPU | VRAM | Empfohlene Modelle |
|-----|------|--------------------|
| T4 | 15 GB | LTX-2 Distilled FP8, Wan 5B (480p) |
| L4/A10 | 24 GB | LTX-2 Distilled, Wan 14B (720p) |
| A100 | 40+ GB | LTX-2 Dev 19B, Wan 14B (1080p) |

## Troubleshooting

| Problem | Loesung |
|---------|---------|
| CUDA Out of Memory | Memory Cleanup Cell ausfuehren, Aufloesung reduzieren |
| LoRA nicht sichtbar | Im UI auf "Refresh" klicken, Ordner pruefen |
| CivitAI Download fehlgeschlagen | API Key setzen, URL pruefen |
| Gradio URL laedt nicht | 1-2 Min warten, URL aus Output kopieren |
| Module not found | Dependencies Cell nochmal ausfuehren |

## Links

- [WanGP Repository](https://github.com/deepbeepmeep/Wan2GP)
- [WanGP LoRA Dokumentation](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/LORAS.md)
- [WanGP Changelog](https://github.com/deepbeepmeep/Wan2GP/blob/main/docs/CHANGELOG.md)
- [CivitAI](https://civitai.com)

## Lizenz

Dieses Projekt folgt der Lizenz des Original WanGP Projekts.

## Credits

- **WanGP**: [deepbeepmeep](https://github.com/deepbeepmeep)
- **Colab Notebook**: HaremOverlord
