# Sử dụng image jupyter/base-notebook làm nền
FROM jupyter/base-notebook:latest 

USER root

RUN apt-get update && \
    apt-get install -y openjdk-8-jdk && \
    rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64

RUN pip install pyspark==3.1.1 pandas matplotlib scipy scikit-learn torch torchvision torchaudio \
    && fix-permissions "$CONDA_DIR" \
    && fix-permissions "/home/$NB_USER"

USER $NB_USER