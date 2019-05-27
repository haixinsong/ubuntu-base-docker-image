# Janus WebRTC Docker image

## What is it

This is a Docker image for [janus-gateway](https://github.com/meetecho/janus-gateway)

## How to use

### build it yourself

`docker build . --no-cache -t nediiii/janus`

### pull from docker hub

`docker pull nediiii/janus`

It doesn't run the `janus` by default it you just start the container without any command.
It just install `janus` on it , you should customize it to suit your demand.
If you want to test the janus, you can try `janus-gstreamer`.Or, do the following.

1. run the container and attach it

   `docker run --rm -it -p 8000:8000 -p 8088:8088 nediiii/janus`

2. install gstreamer for janus-demo

    attention: `gstreamer1.0-plugins-bad` will cause conflict with janus

    ```bash
    apt-get update && \
    apt-get install -y \
    libgstreamer1.0-0 \
    gstreamer1.0-plugins-base \
    gstreamer1.0-plugins-good \
    gstreamer1.0-libav \
    gstreamer1.0-doc \
    gstreamer1.0-tools \
    gstreamer1.0-x \
    gstreamer1.0-alsa \
    gstreamer1.0-gl \
    gstreamer1.0-gtk3 \
    gstreamer1.0-qt5 \
    gstreamer1.0-pulseaudio
    ```

3. start janus server

    ```bash
    cd /opt/janus/bin
    ./janus &
    ```

4. start python webserver at port 8000

    ```bash
    cd /opt/janus/share/janus/demos/
    python -m SimpleHTTPServer 8000 &
    ```

5. start gstreamer to get the testsrc for audio and video

    ```bash
    cd /opt/janus/share/janus/streams
    chmod +x test_gstreamer_1.sh
    ./test_gstreamer_1.sh &
    ```

6. than , you can visit janus-demo in your browser , which typicaly [localhost:8000](localhost:8000)
    the Demo `Echo Test` and `Streaming` work fine , the other I did not test.

## How to dev

just do what ever you want.
There is nothing I hide.
