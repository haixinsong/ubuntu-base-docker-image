# Janus WebRTC with GStreamer Docker image

## What is it

This is a Docker image for [janus-gateway](https://github.com/meetecho/janus-gateway) and [GStreamer](https://gstreamer.freedesktop.org/)

## How to use

### build it yourself

`docker build . --no-cache -t nediiii/janus-gstreamer`

### pull from docker hub

`docker pull nediiii/janus-gstreamer`

As you can see in `Dockerfile`, it doesn't run the anything but `/bin/sh` by default when you just start the container without any command.
If you want to test the janus demo, do the following.

1. run the container and attach it

   `docker run --rm -it -p 8000:8000 -p 8088:8088 nediiii/janus-gstreamer`

2. start janus server

    ```bash
    cd /opt/janus/bin
    ./janus &
    ```

3. start python webserver at port 8000

    ```bash
    cd /opt/janus/share/janus/demos/
    python -m SimpleHTTPServer 8000 &
    ```

4. start gstreamer to get the testsrc for audio and video

    ```bash
    cd /opt/janus/share/janus/streams
    chmod +x test_gstreamer_1.sh
    ./test_gstreamer_1.sh &
    ```

5. than , you can visit janus-demo in your browser , which typicaly [localhost:8000](localhost:8000)
    the Demo `Echo Test` and `Streaming` work fine (!!important: make sure you have disabled chrome flags `enable-webrtc-hide-local-ips-with-mdns` [chrome://flags/#enable-webrtc-hide-local-ips-with-mdns](chrome://flags/#enable-webrtc-hide-local-ips-with-mdns)) , the other I did not test.

## How to dev

just do what ever you want.
There is nothing I hide.
