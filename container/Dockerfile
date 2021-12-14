FROM nvidia/cuda:11.0.3-runtime-ubuntu18.04
MAINTAINER David Soichi Nakahashi <sdn03.tech@gmail.com>

ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8

# Setup python packeges
COPY ./Pipfile Pipfile
COPY ./Pipfile.lock Pipfile.lock

RUN set -ex \
    && apt-get update \
    && apt-get -y upgrade \
    && apt-get install -y tzdata

ENV TZ=Asia/Tokyo
RUN apt-get -y install git vim wget curl software-properties-common
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get install -y python3.9 python3.9-distutils python3-pip
RUN python3.9 -m pip install -U --upgrade pip \
    && python3.9 -m pip install -U pip wheel setuptools pipenv
RUN pipenv install --system

# Configuring access to Jupyter
RUN mkdir /opt/notebooks
RUN jupyter notebook --generate-config --allow-root
RUN echo "c.NotebookApp.password = u'sha1:6a3f528eec40:6e896b6e4828f525a6e20e5411cd1c8075d68619'" >> /root/.jupyter/jupyter_notebook_config.py

# Jupyter listens port: 8888
EXPOSE 8888

# Run Jupyter notebook as Docker main process
CMD ["jupyter", "notebook", "--allow-root", "--notebook-dir=/opt/notebooks", "--ip='*'", "--port=8888", "--no-browser"]
