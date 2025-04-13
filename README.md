# Team 16 - TalkSHOW: Generating Holistic 3D Human Motion from Speech

Contributors - Abinaya Odeti , Shipra , Shravani , Vishal

![teaser](visualise/teaser_01.png)

## About

This repository hosts the implementation of "TalkSHOW: A Speech-to-Motion Translation System", which maps raw audio input to full-body 3D motion using the SMPL-X model. It enables synchronized generation of expressive human body motion (including face, hands, and body) from speech input — supporting real-time animation, virtual avatars, and digital storytelling.

##  Highlights

Translates raw .wav audio into natural whole-body motion (jaw, pose, expressions, hands) using deep learning.

Based on SMPL-X model for realistic 3D human mesh generation.

Modular pipeline with support for face-body composition.

Visualization with OpenGL & FFmpeg for final rendered video.

End-to-end customizable configuration with audio models, latent generation, and rendering.

##  Prerequisites

Python 3.7+

Anaconda for environment management

Install required packages:

```bash
pip install -r requirements.txt
```
Install FFmpeg

➤ Extract the FFmpeg ZIP and add its bin folder to System PATH


## Getting started

The visualization code was test on `Windows 10`, and it requires:

* Python 3.7
* conda3 or miniconda3
* CUDA capable GPU (one is enough)



### 1. Setup and Steps

Clone the repo:
  ```bash
  git clone https://github.com/YOUR_USERNAME/TALKSHOW-speech-to-motion-translation-system.git
  cd TalkSHOW
  ```  
Create conda environment:
```bash
conda create -n talkshow python=3.7 -y
conda activate talkshow
pip install -r requirements.txt
```

### 2.Download models
Download or place the required checkpoints:
Download [**pretrained models**](https://drive.google.com/file/d/1bC0ZTza8HOhLB46WOJ05sBywFvcotDZG/view?usp=sharing),
unzip and place it in the TalkSHOW folder, i.e. ``path-to-TalkSHOW/experiments``.

Download [**smplx model**](https://drive.google.com/file/d/1Ly_hQNLQcZ89KG0Nj4jYZwccQiimSUVn/view?usp=share_link) (Please register in the official [**SMPLX webpage**](https://smpl-x.is.tue.mpg.de) before you use it.)
and place it in ``path-to-TalkSHOW/visualise/smplx_model``.
To visualise the test set and generated result (in each video, left: generated result | right: ground truth).
The videos and generated motion data are saved in ``./visualise/video/body-pixel``:

SMPLX Model Weights – visualise/smplx_model/SMPLX_NEUTRAL_2020.npz

Extra joints, regressors, YAML configs – inside visualise/smplx_model/

Also, ensure vq_path in body_pixel.json points to a valid .pth model (in ./experiments/.../ckpt-*.pth)


###  3.🎙️ Running Inference

To generate a 3D animated video from an audio file:
```bash
python scripts/demo.py \
  --config_file ./config/body_pixel.json \
  --infer \
  --audio_file ./demo_audio/1st-page.wav \
  --id 0 \
  --whole_body
```
Change Input
Replace --audio_file value with your own .wav file path.


### 4. Output
The final 3D animated video will be saved under:
```bash
visualise/video/body-pixel2/<audio_file_name>/1st-page.mp4
```
The exact command you used to run the project
```bash 
python scripts/demo.py --config_file ./config/body_pixel.json --infer --audio_file ./demo_audio/1st-page.wav --id 0 --whole_body
```

### Contact

For issues or questions, raise an issue or contact the contributors directly!
