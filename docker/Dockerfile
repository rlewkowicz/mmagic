FROM nvidia/cuda:11.8.0-devel-ubuntu22.04

# 6 years worth of CUDA arch. 2060+
ENV TORCH_CUDA_ARCH_LIST="7.5 8.6 8.9"
ENV TORCH_NVCC_FLAGS="-Xfatbin -compress-all"

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC
RUN apt-get update && apt-get install -y git python3 python3-pip ninja-build libglib2.0-0 libsm6 libxrender-dev libxext6 libgl1-mesa-glx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/open-mmlab/mmagic.git /mmagic
WORKDIR /mmagic
ENV FORCE_CUDA="1"
RUN pip install --upgrade pip
RUN pip install openmim
RUN pip install torch==2.4.1 torchvision==0.19.1 torchaudio==2.4.1 --index-url https://download.pytorch.org/whl/cu118
RUN mim install mmcv=="2.1.0"
RUN pip install -r requirements.txt
RUN pip install --no-cache-dir -e .

RUN pip install --upgrade --force-reinstall diffusers==0.24
RUN pip install --upgrade --force-reinstall numpy==1.23.5
RUN pip install --upgrade --force-reinstall huggingface_hub[cli]==0.25.2
