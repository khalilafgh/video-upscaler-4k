# Video Upscaler to 4K

Upscale your animation videos to 4K resolution using Real-ESRGAN AI model.

**Input:** 1280×720 (720p)  
**Output:** 3840×2160 (4K)

## Features

✨ AI-powered upscaling with Real-ESRGAN  
🚀 GPU acceleration support (NVIDIA CUDA)  
🎬 Preserves original video FPS  
⚡ Efficient tile-based processing  
📊 Progress tracking  

## Requirements

- Python 3.8+
- NVIDIA GPU (recommended) or CPU (slower)
- 8GB+ RAM (16GB+ recommended for 4K)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/khalilafgh/video-upscaler-4k.git
cd video-upscaler-4k
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

**For GPU support (NVIDIA):**
```bash
# Install CUDA-enabled PyTorch
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

## Usage

### Basic Usage

```bash
python upscale_video.py input_video.mp4
```

This will create `output_4k.mp4` in the current directory.

### Custom Output Path

```bash
python upscale_video.py input_video.mp4 -o my_upscaled_video.mp4
```

### Adjust Tile Size (for better quality or memory constraints)

```bash
# Lower tile size = less memory but slower
python upscale_video.py input_video.mp4 --tile 300

# Higher tile size = faster but more memory
python upscale_video.py input_video.mp4 --tile 500
```

## Performance

- **GPU (RTX 3080):** ~30-60 seconds per minute of video
- **GPU (RTX 2060):** ~2-3 minutes per minute of video
- **CPU:** ~10-20 minutes per minute of video

*Times vary based on tile size and system specs*

## Troubleshooting

### Out of Memory Error
Reduce the tile size:
```bash
python upscale_video.py input_video.mp4 --tile 200
```

### CUDA/GPU Not Detected
The script will automatically fall back to CPU. For GPU support:
```bash
# Verify CUDA installation
python -c "import torch; print(torch.cuda.is_available())"
```

### Slow Performance
- Ensure you're using GPU (check output logs)
- Increase tile size if you have enough VRAM
- Close other applications to free up memory

## Supported Formats

- MP4, AVI, MOV, MKV, FLV, WebM, and most video formats supported by OpenCV

## Model Details

Uses **RealESRGAN_x4plus** model:
- 4x upscaling factor
- Trained on diverse images/animation
- Excellent for clean animation content
- Automatically downloaded on first use (~65MB)

## License

MIT

## Notes

- Processing large videos takes time - plan accordingly
- Output quality depends on input video quality
- For best results, ensure good lighting/quality in source animation
