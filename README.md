For these workflows:

InstantID_FaceRec_STYLE_Zetalvx.json, 
InstantID_SingleImageFaceRecToImage_Zetalvx.json, 
InstantID_depth_FaceSwap_Inpainting_zetalvx.json, 
InstantID_depth_FaceSwap_Zetalvx.json, 

INSTANTID – REQUIRED FILES AND PATHS (COMFYUI)

To run InstantID / IPAdapter workflows correctly in ComfyUI, the following models and dependencies are required.

---

INSTANTID CONTROLNET

Location:

/ComfyUI/models/controlnet/instantid-controlnet.safetensors

Download:
[https://huggingface.co/xingren23/comfyflow-models/resolve/8297c11e55592e513093be0a4085dd666d3789e4/controlnet/instantid-controlnet.safetensors?download=true](https://huggingface.co/xingren23/comfyflow-models/resolve/8297c11e55592e513093be0a4085dd666d3789e4/controlnet/instantid-controlnet.safetensors?download=true)

---

CONTROL LORA DEPTH RANK256

Location:

/ComfyUI/models/controlnet/control-lora-depth-rank256.safetensors

Download:
[https://huggingface.co/stabilityai/control-lora/resolve/main/control-LoRAs-rank256/control-lora-depth-rank256.safetensors?download=true](https://huggingface.co/stabilityai/control-lora/resolve/main/control-LoRAs-rank256/control-lora-depth-rank256.safetensors?download=true)

---

IP-ADAPTER (InstantID)

Location:

/ComfyUI/models/instantid/ip-adapter.bin

Repository:
[https://huggingface.co/InstantX/InstantID](https://huggingface.co/InstantX/InstantID)

Direct download:
[https://huggingface.co/InstantX/InstantID/resolve/main/ip-adapter.bin?download=true](https://huggingface.co/InstantX/InstantID/resolve/main/ip-adapter.bin?download=true)

---

INSIGHTFACE (Face Analysis)

Required folder:

/ComfyUI/models/insightface/antelopev2

Download release:
[https://github.com/deepinsight/insightface/releases](https://github.com/deepinsight/insightface/releases)

Extract the **antelopev2** folder inside `models/insightface`.

---

CLIP VISION MODEL

Location:

/ComfyUI/models/clip_vision/open_clip_model.safetensors

Download:
[https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/clip_vision/clip_vision_h.safetensors](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged/blob/main/split_files/clip_vision/clip_vision_h.safetensors)

---

PYTHON DEPENDENCIES TO INSTALL IN THE COMFYUI ENVIRONMENT

Install inside the ComfyUI virtual environment:

venv311/bin/python -m pip install insightface onnxruntime-gpu opencv-python

Installed libraries:

* insightface
* onnxruntime-gpu
* opencv-python

---

CUSTOM NODES TO INSTALL FROM THE COMFYUI MANAGER

ComfyUI_IPAdapter_plus
[https://github.com/cubiq/ComfyUI_IPAdapter_plus](https://github.com/cubiq/ComfyUI_IPAdapter_plus)

ComfyUI_InstantID
[https://github.com/cubiq/ComfyUI_InstantID](https://github.com/cubiq/ComfyUI_InstantID)

---

Some additional dependencies or models, if missing, may be automatically downloaded the first time the workflow is executed.
