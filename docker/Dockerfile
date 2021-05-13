FROM nvidia/cuda:10.1-cudnn7-devel-ubuntu16.04

# デフォルトの locale `C` を `C.UTF-8` に変更する
ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
# タイムゾーンを日本時間に変更
ENV TZ Asia/Tokyo

COPY . /tmp
WORKDIR /tmp

ENV PYTHON_VERSION 3.8.2
ENV HOME /root
ENV PYTHON_ROOT $HOME/local/python-$PYTHON_VERSION
ENV PATH $PYTHON_ROOT/bin:$PATH
ENV PYENV_ROOT $HOME/.pyenv

RUN export DEBIAN_FRONTEND=noninteractive && \
     apt-get -y update && \
     apt-get -y upgrade && \
     apt-get -y install tzdata
RUN apt-get -y install git make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev && \
    apt-get -y install wget curl vim llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev && \
    git clone https://github.com/pyenv/pyenv.git $PYENV_ROOT && \
    $PYENV_ROOT/plugins/python-build/install.sh && \
    /usr/local/bin/python-build -v $PYTHON_VERSION $PYTHON_ROOT && \
    rm -rf $PYENV_ROOT && \
    pip install --upgrade pip && \
    pip install jupyter click numpy matplotlib seaborn pandas scikit-learn && \
    pip install tensorflow-gpu keras
