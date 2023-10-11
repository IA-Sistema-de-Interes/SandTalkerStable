
      Open In Colab   Hugging Face Spaces   sd webui-colab   Replicate

Wenxuan Zhang *,1,2   Xiaodong Cun *,2  Xuan Wang 3  Yong Zhang 2  Xi Shen 2 
Yu Guo1   Ying Shan 2   Fei Wang 1  

1 Xi'an Jiaotong University   2 Tencent AI Lab   3 Ant Group  

CVPR 2023

sadtalker

TL;DR:       single portrait image 🙎‍♂️      +       audio 🎤       =       talking head video 🎞.


🔥 Highlight
🔥 The extension of the stable-diffusion-webui is online. Checkout more details here.
 sadtalker-webui.mp4 
🔥 full image mode is online! checkout here for more details.
still+enhancer in v0.0.1	still + enhancer in v0.0.2	input image @bagbag1815
 still_e_n.mp4 
 full_body_2.bus_chinese_enhanced.mp4 

🔥 Several new mode, eg, still mode, reference mode, resize mode are online for better and custom applications.

🔥 Happy to see more community demos at bilibili, Youtube and twitter #sadtalker.

📋 Changelog (Previous changelog can be founded here)
[2023.06.05]: release a new 512 beta face model. Fixed some bugs and improve the performance.

[2023.04.15]: Adding automatic1111 colab by @camenduru, thanks for this awesome colab: sd webui-colab.

[2023.04.12]: adding a more detailed sd-webui installation document, fixed reinstallation problem.

[2023.04.12]: Fixed the sd-webui safe issues becasue of the 3rd packages, optimize the output path in sd-webui-extension.

[2023.04.08]: ❗️❗️❗️ In v0.0.2, we add a logo watermark to the generated video to prevent abusing since it is very realistic.

[2023.04.08]: v0.0.2, full image animation, adding baidu driver for download checkpoints. Optimizing the logic about enhancer.

🚧 TODO
Previous TODOs
 Audio-driven Anime Avatar.
 training code of each componments.
If you have any problem, please view our FAQ before opening an issue.
⚙️ 1. Installation.
Tutorials from communities: 中文windows教程 | 日本語コース

Linux:
Installing anaconda, python and git.

Creating the env and install the requirements.

git clone https://github.com/Winfredy/SadTalker.git

cd SadTalker 

conda create -n sadtalker python=3.8

conda activate sadtalker

pip install torch==1.12.1+cu113 torchvision==0.13.1+cu113 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu113

conda install ffmpeg

pip install -r requirements.txt

### tts is optional for gradio demo. 
### pip install TTS
Windows (中文windows教程):
Install Python 3.10.6, checking "Add Python to PATH".
Install git manually (OR scoop install git via scoop).
Install ffmpeg, following this instruction (OR using scoop install ffmpeg via scoop).
Download our SadTalker repository, for example by running git clone https://github.com/Winfredy/SadTalker.git.
Download the checkpoint and gfpgan below↓.
Run start.bat from Windows Explorer as normal, non-administrator, user, a gradio WebUI demo will be started.
Macbook:
More tips about installnation on Macbook and the Docker file can be founded here

📥 2. Download Trained Models.
You can run the following script to put all the models in the right place.

bash scripts/download_models.sh
Other alternatives:

we also provide an offline patch (gfpgan/), thus, no model will be downloaded when generating.

Google Driver: download our pre-trained model from this link (main checkpoints) and gfpgan (offline patch)

Github Release Page: download all the files from the lastest github release page, and then, put it in ./checkpoints.

百度云盘: we provided the downloaded model in checkpoints, 提取码: sadt. And gfpgan, 提取码: sadt.

Model Details
🔮 3. Quick Start (Best Practice).
WebUI Demos:
Online: Huggingface | SDWebUI-Colab | Colab

Local Autiomatic1111 stable-diffusion webui extension: please refer to Autiomatic1111 stable-diffusion webui docs.

Local gradio demo: Similar to our hugging-face demo can be run by:

## you need manually install TTS(https://github.com/coqui-ai/TTS) via `pip install tts` in advanced.
python app.py
Local windows gradio demo: just double click webui.bat, the requirements will be installed automatically.

Manually usages:
Animating a portrait image from default config:
python inference.py --driven_audio <audio.wav> \
                    --source_image <video.mp4 or picture.png> \
                    --enhancer gfpgan 
The results will be saved in results/$SOME_TIMESTAMP/*.mp4.

Full body/image Generation:
Using --still to generate a natural full body video. You can add enhancer to improve the quality of the generated video.

python inference.py --driven_audio <audio.wav> \
                    --source_image <video.mp4 or picture.png> \
                    --result_dir <a file to store results> \
                    --still \
                    --preprocess full \
                    --enhancer gfpgan 
More examples and configuration and tips can be founded in the >>> best practice documents <<<.

🛎 Citation
If you find our work useful in your research, please consider citing:

@article{zhang2022sadtalker,
  title={SadTalker: Learning Realistic 3D Motion Coefficients for Stylized Audio-Driven Single Image Talking Face Animation},
  author={Zhang, Wenxuan and Cun, Xiaodong and Wang, Xuan and Zhang, Yong and Shen, Xi and Guo, Yu and Shan, Ying and Wang, Fei},
  journal={arXiv preprint arXiv:2211.12194},
  year={2022}
}
💗 Acknowledgements
Facerender code borrows heavily from zhanglonghao's reproduction of face-vid2vid and PIRender. We thank the authors for sharing their wonderful code. In training process, We also use the model from Deep3DFaceReconstruction and Wav2lip. We thank for their wonderful work.

See also these wonderful 3rd libraries we use:

Face Utils: https://github.com/xinntao/facexlib
Face Enhancement: https://github.com/TencentARC/GFPGAN
Image/Video Enhancement:https://github.com/xinntao/Real-ESRGAN
🥂 Extensions:
SadTalker-Video-Lip-Sync from @Zz-ww: SadTalker for Video Lip Editing
🥂 Related Works
StyleHEAT: One-Shot High-Resolution Editable Talking Face Generation via Pre-trained StyleGAN (ECCV 2022)
CodeTalker: Speech-Driven 3D Facial Animation with Discrete Motion Prior (CVPR 2023)
VideoReTalking: Audio-based Lip Synchronization for Talking Head Video Editing In the Wild (SIGGRAPH Asia 2022)
DPE: Disentanglement of Pose and Expression for General Video Portrait Editing (CVPR 2023)
3D GAN Inversion with Facial Symmetry Prior (CVPR 2023)
T2M-GPT: Generating Human Motion from Textual Descriptions with Discrete Representations (CVPR 2023)
📢 Disclaimer
This is not an official product of Tencent. This repository can only be used for personal/research/non-commercial purposes.

LOGO: color and font suggestion: ChatGPT, logo font：Montserrat Alternates .

All the copyright of the demo images and audio are from communities users or the geneartion from stable diffusion. Free free to contact us if you feel uncomfortable.
