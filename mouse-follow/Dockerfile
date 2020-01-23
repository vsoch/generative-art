FROM ubuntu:18.04

# docker build -t processing-example .

RUN apt-get update && apt-get install -y wget openjdk-8-jdk build-essential
WORKDIR /code
RUN wget http://py.processing.org/processing.py-linux64.tgz && \ 
    tar -xzvf processing.py-linux64.tgz && \
    mv processing.py-3056-linux64/processing-py.jar processing-py.jar && \
    chmod +x processing-py.jar && \
    rm -rf processing.py-3056-linux64
COPY . /code
ENTRYPOINT ["java"]
CMD ["-jar", "processing-py.jar", "/code/mouse-follow.py"]
