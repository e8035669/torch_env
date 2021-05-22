FROM manjarolinux/base

RUN pacman -Syu --noconfirm pacaur cuda tmux zip tar git fakeroot vi \
    opencv bash-completion\
    python-pytorch-opt-cuda python-pillow python-scipy python-tqdm \
    python-pip python-seaborn tensorboard python-opencv python-pandas && \
    pacman -Scc --noconfirm

RUN useradd -m -s /bin/bash packager && \
    echo "packager ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/packager

USER packager
WORKDIR /home/packager/
ENV CUDA_HOME "/opt/cuda"

RUN pacaur -S --noconfirm --noedit python-av python-pycocotools && \
    pacaur -Scc --noconfirm

RUN git clone https://aur.archlinux.org/python-torchvision.git && \
    cd python-torchvision && \
    makepkg --nocheck && \
    pacaur -U --noconfirm --noedit python-torchvision-cuda-*.zst && \
    cd /home/packager && \
    rm -rf python-torchvision


USER root
WORKDIR /root/

RUN git clone https://github.com/ultralytics/yolov3 && \
    cd yolov3 && \
    pip --no-cache-dir install thop opencv-python tensorboard-data-server \
    torchsummary sklearn

WORKDIR /root/
RUN pacaur -Scc --noconfirm && \
    rm /etc/sudoers.d/packager && \
    userdel -r packager && \
    pacaur -Rdd --noconfirm nvidia-utils

WORKDIR /root/
CMD ["/bin/bash"]
