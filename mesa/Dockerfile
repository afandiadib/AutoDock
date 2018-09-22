FROM ubuntu
MAINTAINER "Adib Afandi bin Abdullah <fendy90.oscura@gmail.com>"
RUN apt-get update && \
    apt-get -y install wget libx11-6 libgl1-mesa-glx libglu1-mesa libxmu6 libxi6 libxcursor1 && \

# Autodock Tools
    wget --quiet http://mgltools.scripps.edu/downloads/downloads/tars/releases/REL1.5.6/mgltools_x86_64Linux2_1.5.6.tar.gz && \
    tar -xzvf mgltools_x86_64Linux2_1.5.6.tar.gz -C /opt/ && \
    (cd /opt/mgltools_x86_64Linux2_1.5.6 && ./install.sh) && \ 

# vina
    wget http://vina.scripps.edu/download/autodock_vina_1_1_2_linux_x86.tgz && \
    tar -xvf autodock_vina_1_1_2_linux_x86.tgz -C /opt/ && \

# cleanup
    apt-get -y purge wget && \
    apt-get -y autoremove && apt-get -y clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm *.tgz *.tar.gz

ENV PATH="/opt/mgltools_x86_64Linux2_1.5.6/bin:${PATH}"
ENV PATH="/opt/autodock_vina_1_1_2_linux_x86/bin:${PATH}"
