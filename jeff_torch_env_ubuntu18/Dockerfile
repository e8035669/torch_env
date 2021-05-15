FROM nvidia/cuda:11.1-cudnn8-devel-ubuntu18.04

RUN apt update -y \
 && apt install -y python3-pip tmux sudo vim \
 && update-alternatives --install /usr/bin/python python /usr/bin/python3.6 10 \
 && python -m pip --no-cache-dir install -U pip \
 && python -m pip --no-cache-dir install torch==1.8.1+cu111 torchvision==0.9.1+cu111 -f https://download.pytorch.org/whl/torch_stable.html \
 && python -m pip --no-cache-dir install matplotlib numpy opencv-python Pillow PyYAML scipy tqdm tensorboard seaborn pandas thop pycocotools \
 && apt-get clean -y

RUN useradd -m -s /bin/bash -u 1000 -U jeff \
 && echo "jeff ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/jeff

USER jeff
WORKDIR /home/jeff
CMD ["/bin/bash"]


