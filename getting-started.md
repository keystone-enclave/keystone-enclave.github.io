---
layout: page
width: expand
hero:
    title:
    subtitle: An Open Framework for Architecting Trusted Execution Environments
    image: keystone-logo-D.png
    search: false
---

Keystone can be tested in two main ways:

## Full Development Environment

Setup a full Keystone test and development environment (1hr+) with the
instructions in our
[documentation](http://docs.keystone-enclave.org/en/dev/Getting-Started/index.html)

## Docker Image

Download and run tests in our Docker image (10min).

```
wget https://keystone-enclave.eecs.berkeley.edu/files/keystone-sample-image_docker.tgz
docker load --input keystone-sample-image_docker.tgz
docker run --name keystone-sample -it keystone-sample-image
```

Now, run tests in the container. See our [documentation](http://docs.keystone-enclave.org/en/dev/Getting-Started/QEMU-Run-Tests.html) for details.

```
  # In the container
  su keystone
  cd ~/keystone
  make run-tests
```