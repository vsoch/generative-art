# Testing Mouse Follow

This is a small Python file to be used with Processing to test a container
build. Namely, we can run [Processing on the command line](https://py.processing.org/tutorials/command-line/) via basic java. 

# Usage

## Local

I am using a [Makefile](Makefile) to run the application, and note that I've
extracted the jar as follows:

```bash
here=${PWD}
cd /tmp
wget http://py.processing.org/processing.py-linux64.tgz
tar -xzvf processing.py-linux64.tgz
mv processing.py-3056-linux64/processing-py.jar $HERE/processing-py.jar
rm -rf /tmp/processing.py-3056-linux64
```

Note that this is for x64 systems. You'd also need java installed:

```bash
sudo apt-get update && apt-get install -y default-jdk
```

so then I can just run:

```bash
make
```

## Containers

Singularity containers can support the graphics. First we will build from
Docker (and I'm doing this because I intend to create Docker containers
that can generate images without needing the display.

```bash
docker build -t processing-example .
```

And then build and run with Singularity.

```bash
singularity build example.sif docker-daemon://processing-example:latest
singularity run example.sif
```

It should work the same as if you just ran it locally.
