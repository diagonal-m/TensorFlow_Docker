# TensorFlow_Docker
DockerでTensorFlowの環境を構築する


```bash
$ git clone git@github.com:diagonal-m/TensorFlow_Docker.git
$ cd TensorFlow_Docker
$ ls
$ README.md  docker/
$ docker build -f docker/Dockerfile -t tensorflow --no-cache .
$ docker run --gpus all --name tensorflow -it -d -v $(pwd):/tmp tensorflow:latest /bin/bash
```
