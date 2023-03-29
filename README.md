# Notebooks for RunPod

### Text to Video Zero

Please use with more than 20GB GPU

https://runpod.io/gsc?template=fvddsynfnn&ref=iqi9iy8y

```py
%cd /content
!apt update && apt install -y libgl1 git-lfs
!git lfs install
!pip install imageio==2.25.1 opencv-python==4.7.0.72 scipy==1.10.1 scikit-image==0.19.3 basicsr==1.4.2
!pip install -q gradio==3.23.0 decord==0.6.0 diffusers==0.14.0 accelerate==0.17.0 safetensors==0.2.7 einops==0.6.0 transformers==4.26.0
!pip install -q xformers==0.0.16 triton==2.0.0
!git clone -b pro https://gitlab.com/camenduru/text2-video-zero


model = "plasmo/woolitize-768sd1-5"
model = model.replace('/', '\/')
!sed -i -e 's/runwayml\/stable-diffusion-v1-5/{model}/g' /content/text2-video-zero/model.py 


%cd /content/text2-video-zero
!python app.py
```
