# tensorflow_docker

### If you want to pull already built docker imag


### How to use?
  - Clone the repo or download Dockerfile
  - Navigate to the directory where you have the Dockerfile
  - Build the docker image with your username & preferred image name:
    - docker build -t your_docker_username/prefered_imagename:1.5.0-devel . --no-cache=true
    - In my case it was, docker build -t dinesh001/tensorflow_docker:1.5.0-devel . --no-cache=true
  - Commit
    - docker commit container_ID repository_name:tag #dinesh001/tensorflow_docker:1.5.0-devel
  - Push the docker image to your docker hub. (Optional, if you want the image available at hub)
    - Find the docker image id
      - Type docker images - you'll se a list of images with IMAGE ID column
    - docker tag IMAGE_ID repository_name:tag (In my case, it was docker tag 91b81cbc9d89 dinesh001/tensorflow_docker:1.5.0-devel)
    - Login to docker hub
      - Type "docker login" in your terminal and enter your details.
    - Type "docker push repository_name:tag" (in my case, it was docker push dinesh001/tensorflow_docker:1.5.0-devel)

### Other

  - I was getting error when using export inference graph [bug here](https://github.com/tensorflow/models/issues/2861), I replaced line.71 in exporter.py from rewriter_config_pb2.RewriterConfig(optimize_tensor_layout=True) to rewrite_options = rewriter_config_pb2.RewriterConfig(layout_optimizer=True)


### References
  - [repo](https://github.com/sofwerx/android-tensorflow-object-detection/blob/master/Dockerfile) with additions/modifications based on [tensorflow installation](https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md)
