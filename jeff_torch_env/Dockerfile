FROM e8035669/torch_env

RUN useradd -m -s /bin/bash -u 1000 -U jeff \
 && echo "jeff ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/jeff

USER jeff
WORKDIR /home/jeff
CMD ["/bin/bash"]


