FROM nvidia/cuda:10.2-devel-ubuntu18.04

RUN apt update -y \
 && apt install -y python3-pip tmux sudo vim \
 && update-alternatives --install /usr/bin/python python /usr/bin/python3.6 10 \
 && python -m pip --no-cache-dir install -U pip \
 && python -m pip --no-cache-dir install torch torchvision \
 && python -m pip --no-cache-dir install matplotlib numpy opencv-python-headless \
    Pillow PyYAML scipy tqdm tensorboard seaborn pandas thop pycocotools scikit-learn \
    torchsummary \
 && apt-get clean -y

RUN useradd -m -s /bin/bash -u 1000 -U jeff \
 && echo "jeff ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/jeff

USER jeff
WORKDIR /home/jeff
CMD ["/bin/bash"]


