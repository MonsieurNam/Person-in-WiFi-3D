# 🛰️ Person-in-WiFi 3D  
**End-to-End Multi-Person 3D Pose Estimation with Wi-Fi**

---

## 📘 Overview
Wi-Fi signals, unlike cameras, provide **privacy protection** and **occlusion resilience**, making them ideal for scenarios such as **smart homes**, **elderly care**, and **virtual reality**.  
Recent years have seen remarkable progress in single-person and multi-person pose estimation — both 2D and 3D.  
**Person-in-WiFi 3D** takes a step further by introducing a **pioneering Wi-Fi-based system** capable of **multi-person 3D pose estimation**.

### 🔍 Key Features
- **Multiple Wi-Fi devices** to enhance spatial reflection capture.  
- **Transformer-based architecture** for **end-to-end estimation**.  
- **Storage-efficient** and **fast**, compared to previous versions.  
- **High accuracy:**  
  - 91.7 mm (1 person)  
  - 108.1 mm (2 persons)  
  - 125.3 mm (3 persons)

A dataset of **97K+ frames** collected from **7 volunteers** in a **4m × 3.5m** area demonstrates the system’s performance comparable to **camera-based** and **millimeter-wave radar** methods.

---

<p align="center">
  <img src="demo/demo mini.gif" width="900" height="300" alt="demo gif">
</p>
---

## ⚙️ Prerequisites
- **Linux (Ubuntu 20.04+ recommended)**  
- **Python 3.7+**  
- **PyTorch 1.8+**  
- **CUDA 10.1+**  
- **MMCV, MMDetection**

---

## 🚀 Installation Guide

### Step 1. System Setup
```bash
apt update
apt install -y git python3-pip zip unzip tmux
pip install gdown
```
### Step 2. Install Miniconda
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
export PATH="/root/miniconda3/bin:$PATH"
conda --version
/root/miniconda3/bin/conda init bash
source ~/.bashrc
```

---

## For environment and dataset, contact us for more information 
### Step 3. Setup Environment

```
gdown <env>
unzip opera.zip -d miniconda3/envs/
git clone https://github.com/Winter24/Person-in-WiFi-3D
conda activate opera
cd Person-in-WiFi-3D
```

### Step 4. Dataset Preparation
```
#!/bin/bash
curl -L -o wifipose-dataset.zip <link>

mkdir -p data/wifipose
unzip wifipose-dataset.zip -d data/wifipose
```

### Step 5. Some Dependency Installation
```
apt install -y libgl1-mesa-glx libglib2.0-0 libsm6 libxrender1 libxext6
cd third_party/mmdet/
python -m pip install -U pip setuptools wheel
python -m pip install -e .
cd ../..
pip install -r requirements.txt
pip install -e .
python -m pip install 'yapf==0.40.1'
```
If you get:
```
CERTIFICATE_VERIFY_FAILED: unable to get local issuer certificate (_ssl.c:1091)
```
Run:
```
apt install -y ca-certificates
update-ca-certificates
python -m pip install --upgrade pip certifi
```

### Train:
```
python tools/train.py configs/wifi/petr_wifi_linear_fast.py --gpu-id 0 --seed 42 --deterministic
```
