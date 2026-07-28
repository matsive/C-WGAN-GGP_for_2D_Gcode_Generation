## Citation

If you use this repository, please cite:

**Paper:** [Towards generative additive manufacturing: A conditional Wasserstein generative adversarial networks framework for layer-wise point generation and toolpath formation](https://www.sciencedirect.com/science/article/pii/S2950431726000407)
Or 
Ali M, Gopu V, Liao Y, Liu S. Towards generative additive manufacturing: A conditional Wasserstein generative adversarial networks framework for layer-wise point generation and toolpath formation. Additive Manufacturing Frontiers. 2026 Mar 25:200333.



# C-WGAN-GGP_for_2D_Gcode_Generation

C-WGAN-GGP stands for Conditional Wasserstein Generative Adversarial Network with Gaussian Noise and Gradient Penalty. The model employs Gaussian-distributed latent noise as the generator input while using the gradient penalty regularization proposed in WGAN-GP to stabilize adversarial training.

### Open and run in Terminal to install pytorch3d

### 1) Remove old pytorch3d environment
```bash
conda deactivate 2>/dev/null || true
conda env remove -n pytorch3d -y
```

### 2) Create new conda environment with Python 3.10.18
```bash
conda create -n pytorch3d python=3.10.18 pip -y
conda activate pytorch3d
```

### 3) Avoid user-level Python packages leaking into this env
```bash
export PYTHONNOUSERSITE=1
```

### 4) Install PyTorch 2.2.0 with CUDA 12.1
```bash
python -m pip install --upgrade pip setuptools wheel
python -m pip install torch==2.2.0+cu121 torchvision==0.17.0+cu121 torchaudio==2.2.0+cu121 --index-url https://download.pytorch.org/whl/cu121
```

### 5) Install compatible NumPy and PyTorch3D dependencies
```bash
python -m pip install "numpy<2"
python -m pip install fvcore iopath ninja
```

### 6) Install CUDA 12.1 compiler/header packages
```bash
conda install -y -c nvidia/label/cuda-12.1.1 cuda-nvcc cuda-cudart-dev cuda-cccl
```

### 7) Build/install PyTorch3D 0.7.8 from source
```bash
export FORCE_CUDA=1
export CUDA_HOME=$CONDA_PREFIX
export PATH=$CUDA_HOME/bin:$PATH
export MAX_JOBS=2

python -m pip install --no-cache-dir --no-build-isolation "git+https://github.com/facebookresearch/pytorch3d.git@V0.7.8"
```

### 8) Finally install jupyter notebook
```bash
conda activate pytorch3d
export PYTHONNOUSERSITE=1

python -m pip install notebook ipykernel

python -m ipykernel install --user --name pytorch3d --display-name "Python (pytorch3d)"

cd /home/imml/WGAN_toolpath/

jupyter notebook
```

### 9) The scripts

1. CondaEnv_test.ipynb
2. Dataset_Construction.ipynb
3. Training AE code.ipynb (Make sure to change or fix config.yaml)
4. GAN TRAINING AMF.ipynb
5. GAN Inference Gcode.ipynb
6. Matrix 10 AMF.ipynb

gcode_layers_V1.npy can be createcd using code 
or
gcode_layers_V1.npy can be downloaded from : https://drive.google.com/file/d/112dqRrUqYOsUPeD_CcDT8Pvgy-l7Janj/view?usp=drive_link
