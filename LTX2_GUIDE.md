# 🌟 LTX-2 Complete Guide

Ultimate guide for using LTX-2 (the newest and most advanced model) in the Wan2GP Colab notebook.

---

## 🎯 What is LTX-2?

**LTX-2** is the **latest and most advanced video generation model** in Wan2GP, released in early 2025. It's a 19 billion parameter model that significantly improves upon its predecessor LTX Video.

### Key Features:
- 🎬 **Longest videos**: Up to **20 seconds** (241 frames @ 24 FPS)
- 🎵 **Audio generation**: Automatically creates matching soundtracks!
- ⚡ **Very fast**: Distilled version needs only **8 steps**
- 🖼️ **Keyframe control**: Start & end image support
- 🔄 **Sliding window**: Extend videos beyond 20 seconds
- 📐 **Flexible resolutions**: Portrait, landscape, square
- 🎨 **High quality**: State-of-the-art video generation

---

## 📦 Available Models

### 1. **LTX-2 Dev 19B** (Best Quality)

**When to use:**
- When you want maximum quality
- For final productions
- When you have 20+ GB VRAM
- When speed is not critical

**Specifications:**
- Parameters: 19 billion
- Steps: 40 (recommended)
- FPS: 24
- Max duration: 20 seconds (241 frames)
- VRAM: 18-25 GB
- Download size: ~12 GB (FP32) or ~6 GB (FP8)
- Audio: Yes ✅

**HuggingFace:**
- Main: `DeepBeepMeep/LTX-2/ltx-2-19b-dev.safetensors`
- FP8: `DeepBeepMeep/LTX-2/ltx-2-19b-dev-fp8.safetensors`

### 2. **LTX-2 Distilled 19B** (Super Fast)

**When to use:**
- For rapid iterations and testing
- When VRAM is limited
- When you need quick results
- For batch processing

**Specifications:**
- Parameters: 19 billion (distilled)
- Steps: **Only 8!** (5x faster than Dev)
- FPS: 24
- Max duration: 20 seconds (241 frames)
- VRAM: 15-20 GB
- Download size: ~12 GB (FP32) or ~6 GB (FP8)
- Audio: Yes ✅

**HuggingFace:**
- Main: `DeepBeepMeep/LTX-2/ltx-2-19b-distilled.safetensors`
- FP8: `DeepBeepMeep/LTX-2/ltx-2-19b-distilled-fp8.safetensors`

---

## 🎨 Using LTX-2 in the Colab Notebook

### Step 1: Launch the Notebook

Open `Wan2GP_Complete_UI.ipynb` and run all cells:
1. GPU check
2. Mount Google Drive (optional but recommended)
3. Clone repository
4. Install dependencies
5. Apply optimizations
6. Configure models
7. **Start Gradio UI** ← Wait for this!

### Step 2: Access the Interface

After cell 7, you'll see:
```
Running on public URL: https://xxxxx.gradio.live
```
Copy and open this URL in your browser.

### Step 3: Select LTX-2

In the Gradio interface:
1. Find the **"Model"** dropdown
2. Select either:
   - `LTX-2 Dev 19B` (best quality)
   - `LTX-2 Distilled 19B` (fastest)

### Step 4: Configure Settings

Adjust the generation parameters (see recommendations below).

### Step 5: Generate!

Enter your prompt and click Generate.

---

## ⚙️ Recommended Settings

### For T4 GPU (15GB VRAM) - Colab Free

**Fast Preview:**
```yaml
Model: LTX-2 Distilled 19B
Resolution: 512x384 (landscape)
Video Length: 81 frames (~3.4 seconds)
Steps: 8
Guidance Scale: 4.0
Audio: Enabled ✅
```

**Balanced Quality:**
```yaml
Model: LTX-2 Distilled 19B
Resolution: 512x512 (square)
Video Length: 121 frames (~5 seconds)
Steps: 8
Guidance Scale: 4.0
Audio: Enabled ✅
```

### For L4/A10 GPU (24GB VRAM) - Colab Pro

**High Quality:**
```yaml
Model: LTX-2 Dev 19B
Resolution: 640x480
Video Length: 161 frames (~6.7 seconds)
Steps: 30
Guidance Scale: 4.0
Audio: Enabled ✅
```

**Maximum Length:**
```yaml
Model: LTX-2 Distilled 19B
Resolution: 512x384
Video Length: 241 frames (~10 seconds)
Steps: 8
Guidance Scale: 4.0
Audio: Enabled ✅
```

### For A100 GPU (40GB VRAM) - Colab Pro+

**Maximum Quality:**
```yaml
Model: LTX-2 Dev 19B
Resolution: 768x512 (or 1024x576)
Video Length: 241 frames (~10 seconds)
Steps: 40
Guidance Scale: 4.0
Audio: Enabled ✅
FP8: Disabled
```

**Ultra Long (with Sliding Window):**
```yaml
Model: LTX-2 Dev 19B
Resolution: 640x480
Video Length: 481 frames (~20 seconds)
Steps: 40
Guidance Scale: 4.0
Sliding Window: Enabled
Window Size: 241
Overlap: 9
Audio: Enabled ✅
```

---

## 🎵 Audio Features

LTX-2 can generate synchronized audio alongside video!

### Automatic Audio Generation

**How it works:**
Simply enable audio in the settings, and LTX-2 will generate a matching soundtrack based on your text prompt.

**Example:**
```
Prompt: "A jazz band performing in a smoky club, upbeat tempo, energetic"
Audio: Enabled

→ Generates video of jazz band + matching jazz music!
```

### Audio Prompt (Audio-to-Video)

**How it works:**
Upload an audio file (music/sound), and LTX-2 will generate video that matches the audio.

**Steps:**
1. Select "Audio Prompt" mode in UI
2. Upload your audio file (.mp3, .wav, etc.)
3. Add descriptive prompt
4. Generate

**Example:**
```
Audio: [Upload dramatic_music.mp3]
Prompt: "Epic fantasy battle scene matching this soundtrack"

→ Generates video synchronized to your music!
```

### Best Practices for Audio:

**For best results:**
- Include audio-related keywords in prompt:
  - "with upbeat music"
  - "dramatic soundtrack"
  - "peaceful ambient sounds"
- Use appropriate video length (longer for music)
- Enable audio in settings
- Use Guidance Scale: 3.5-4.5 for audio

**Audio keywords to try:**
- Music genres: jazz, classical, rock, electronic, orchestral
- Moods: upbeat, dramatic, peaceful, energetic, melancholic
- Instruments: piano, guitar, drums, violin, synthesizer
- Ambience: nature sounds, city noise, ocean waves, wind

---

## 📝 Prompt Engineering for LTX-2

### General Structure

```
[Subject/Scene] + [Action/Movement] + [Style/Mood] + [Camera/Lighting]
```

### Excellent Prompts for LTX-2:

#### Cinematic Scenes:
```
A dramatic sunset over the ocean, waves crashing against rocks,
seagulls flying overhead, golden hour lighting, cinematic camera movement,
peaceful atmosphere, 4K quality
```

```
A futuristic cyberpunk city at night, neon signs reflecting on wet streets,
flying vehicles passing by, rain falling, moody blue and purple lighting,
slow camera pan, cinematic
```

#### Nature & Landscapes:
```
A misty forest at dawn, sunbeams filtering through ancient trees,
morning fog rolling over the ground, birds flying, peaceful ambiance,
slow camera dolly forward
```

```
Northern lights dancing over a snowy mountain landscape, stars visible,
time-lapse style movement, ethereal greens and purples, majestic, 4K
```

#### Action & Movement:
```
A skateboarder performing tricks in an urban skate park at sunset,
dynamic camera following the action, energetic vibe, warm golden lighting,
slow motion moments
```

```
A dancer performing ballet in an elegant studio, graceful movements,
soft natural lighting from large windows, camera slowly circling, artistic
```

#### Character-Focused:
```
Portrait of an elderly man sitting by a window, reading a book,
gentle afternoon light, dust particles visible in sunbeams, contemplative mood,
slow push-in camera movement
```

```
A young couple walking hand in hand through an autumn park,
leaves falling around them, soft romantic lighting, golden hour,
camera following from behind, warm atmosphere
```

#### With Audio Keywords:
```
A jazz quartet performing in an intimate club, upbeat swing music,
audience silhouettes visible, warm amber lighting, smoke in the air,
dynamic camera moving between musicians
```

```
A thunderstorm over a prairie landscape, lightning flashing,
dramatic thunder sounds, dark ominous clouds, wind blowing grass,
wide cinematic shot, moody atmosphere
```

### Keywords That Work Well:

**Camera Movements:**
- "slow camera pan"
- "dolly forward/backward"
- "camera circling"
- "smooth tracking shot"
- "crane shot"
- "first-person view"

**Lighting:**
- "golden hour lighting"
- "soft natural light"
- "dramatic shadows"
- "backlit"
- "volumetric lighting"
- "neon glow"

**Mood/Style:**
- "cinematic"
- "4K quality"
- "atmospheric"
- "dramatic"
- "peaceful"
- "energetic"
- "moody"

**Movement:**
- "slow motion"
- "time-lapse"
- "dynamic movement"
- "graceful"
- "flowing"

---

## 🎥 Advanced Features

### Keyframe Control

**Start & End Images:**
LTX-2 supports using images as keyframes to control the video.

**Use cases:**
- Morph between two images
- Animate a static image
- Control start and end states

**How to use:**
1. Upload start image (optional)
2. Upload end image (optional)
3. Set video length
4. Generate

**Example:**
```
Start Image: [Portrait of person smiling]
End Image: [Same person laughing]
Prompt: "Smooth transition from smile to laughter, natural expression"
```

### Sliding Window (Long Videos)

**For videos longer than 20 seconds:**
Enable sliding window to generate extended videos.

**Settings:**
- Window Size: 241 frames (how much to generate at once)
- Overlap: 9-17 frames (how much to overlap between windows)

**Example:**
```
Video Length: 481 frames (~20 seconds)
Sliding Window: Enabled
Window Size: 241
Overlap: 9

→ Generates seamless 20-second video!
```

### Resolution Options

**Supported aspect ratios:**
- **Landscape**: 640x480, 768x512, 512x384
- **Portrait**: 480x640, 512x768, 384x512
- **Square**: 512x512, 640x640

**Tips:**
- Use landscape for most scenes
- Portrait for vertical social media
- Square for Instagram/TikTok

---

## ⚡ Performance Tips

### For Fastest Generation:

1. **Use Distilled model** (8 steps only!)
2. **Lower resolution** (512x384)
3. **Shorter videos** (81-121 frames)
4. **FP8 weights** (half the size)
5. **Disable audio** (saves compute)

### For Best Quality:

1. **Use Dev model** (40 steps)
2. **Higher resolution** (768x512 or 1024x576)
3. **More frames** (241+)
4. **Detailed prompts** (describe everything)
5. **Guidance scale 3.5-4.5** (sweet spot)

### Memory Management:

**If you get "CUDA Out of Memory":**
1. Run the memory cleanup cell in notebook
2. Reduce resolution (768→640→512)
3. Reduce frames (241→161→121)
4. Use Distilled instead of Dev
5. Enable FP8 mode
6. Close other Colab tabs

**To prevent OOM:**
- Generate one video at a time
- Clean up between generations
- Use Google Drive for models (persistent)
- Don't load multiple models

---

## 📊 Comparison: LTX-2 vs Other Models

| Feature | LTX-2 Dev | LTX-2 Dist | Wan 2.2 | Hunyuan |
|---------|-----------|------------|---------|---------|
| Max Length | **20s** ✅ | **20s** ✅ | 5s | 10s |
| FPS | 24 | 24 | 8-16 | 24 |
| Audio | **Yes** ✅ | **Yes** ✅ | No | No |
| Steps | 40 | **8** ✅ | 25-50 | 40-60 |
| VRAM | 18-25GB | 15-20GB | 10-15GB | 20-30GB |
| Speed | Medium | **Very Fast** ✅ | Medium | Slow |
| Quality | **Excellent** ✅ | Very Good | Excellent | Excellent |
| Best For | Final outputs | Iteration | Balanced | Motion |

**When to use LTX-2:**
- ✅ Need videos longer than 10 seconds
- ✅ Want audio soundtrack
- ✅ Need fast iterations (Distilled)
- ✅ Want latest technology
- ✅ Have 15+ GB VRAM

**When to use alternatives:**
- Wan 2.2: Better VRAM efficiency, shorter videos
- Hunyuan: Complex motion, character animation
- Qwen: Image generation instead of video

---

## 🐛 Troubleshooting

### Model Won't Load

**Problem:** LTX-2 model fails to load

**Solutions:**
1. Check internet connection (downloads from HF)
2. Ensure enough disk space (~12 GB)
3. Try FP8 version (smaller)
4. Check HuggingFace is accessible
5. Clear cache and retry

### Low Quality Output

**Problem:** Video quality is poor

**Solutions:**
1. Use Dev model instead of Distilled
2. Increase steps (20→30→40)
3. Improve prompt (more details)
4. Try different guidance scale (3-5)
5. Use higher resolution
6. Check if model downloaded correctly

### Audio Not Generated

**Problem:** No audio in output

**Solutions:**
1. Ensure "Audio" is enabled in settings
2. Add audio keywords to prompt
3. Use longer video (audio works better with 5s+)
4. Check audio settings in UI
5. Try Dev model (better audio)

### OOM Errors

**Problem:** CUDA Out of Memory

**Solutions:**
1. **Immediate fix:** Run cleanup cell
2. Use Distilled model (less VRAM)
3. Reduce resolution: 768→640→512→384
4. Reduce frames: 241→161→121→81
5. Enable FP8 mode
6. Close other processes
7. Restart Colab runtime

### Slow Generation

**Problem:** Takes very long to generate

**Solutions:**
1. Use Distilled model (5x faster!)
2. Reduce steps: 40→20→8
3. Use lower resolution
4. Fewer frames
5. Check GPU type (should be T4+, not CPU)
6. Disable audio if not needed

---

## 💡 Tips & Tricks

### Getting Started:
1. **Start with Distilled** for testing
2. **Use short videos first** (81 frames)
3. **Test different prompts** quickly
4. **Then switch to Dev** for final output

### Prompt Tips:
- Be specific about camera movement
- Include lighting/mood descriptors
- Mention time of day
- Add style keywords (cinematic, 4K)
- For audio, describe sound/music

### Quality Tips:
- Use Dev model for finals
- 30-40 steps is sweet spot
- Guidance 3.5-4.5 works best
- Higher resolution = better (if VRAM allows)
- Longer prompts = more control

### Speed Tips:
- Distilled = 5x faster
- Lower res = 2x faster
- Fewer frames = linear speedup
- FP8 = slightly faster
- Disable audio = ~10% faster

---

## 📚 Additional Resources

### Official:
- **Wan2GP Repo**: https://github.com/deepbeepmeep/Wan2GP
- **LTX-2 Models**: https://huggingface.co/DeepBeepMeep/LTX-2
- **Documentation**: `/content/Wan2GP/docs/`

### Community:
- **Example Videos**: Check HuggingFace model card
- **Prompts Collection**: See community discussions
- **Tips & Tricks**: GitHub issues/discussions

---

## 🎯 Quick Reference

### Command Cheat Sheet:

**Start Gradio UI:**
```bash
python wgp.py --share --server-name 0.0.0.0
```

**Memory Cleanup:**
```python
from optimizations import efficient_memory_cleanup
efficient_memory_cleanup()
```

**Check Memory:**
```python
from optimizations import print_memory_stats
print_memory_stats()
```

### Settings Cheat Sheet:

**Fast & Low VRAM:**
- Model: LTX-2 Distilled
- Resolution: 512x384
- Frames: 81
- Steps: 8

**Balanced:**
- Model: LTX-2 Distilled
- Resolution: 640x480
- Frames: 121
- Steps: 8

**Max Quality:**
- Model: LTX-2 Dev
- Resolution: 768x512
- Frames: 241
- Steps: 40

---

**Happy generating with LTX-2! 🎬✨**

*Last updated: 2026-01-11*
*Version: 1.0*
