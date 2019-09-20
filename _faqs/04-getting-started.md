---
title: How do I try Keystone Enclave?
categories: [presale]
---

You can download our Docker image and run tests within 10 minutes (Ubuntu).

```
wget https://keystone-enclave.eecs.berkeley.edu/files/keystone-sample-image_docker.tgz
docker load --input keystone-sample-image_docker.tgz
docker run --name keystone-sample -it keystone-sample-image
```

Run tests in the container

```
# In the container
su keystone
cd ~/keystone
make run-tests
```

See [Documentation](https://docs.keystone-enclave.org/en/latest/Getting-Started/Running-Keystone-with-QEMU.html)
for setting up a full development environment (1hr+).
