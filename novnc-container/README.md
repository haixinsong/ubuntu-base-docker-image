# NoVNC Container

## What is it

This is a Docker image for my Class Project, which can run a GUI app on docker and visit it on browser.
I use noVNC to interact with app, use GStreamer and Janus to support the audio.

## How to use

### build it yourself

`docker build . --no-cache -t nediiii/novnc-continaer`

### pull from docker hub

`docker pull nediiii/novnc-continaer`

As you can see in `Dockerfile`, it just run a supervisord to manage all the process.
If you want to customize it to wrap other app, feel free to modify the supervisord.conf.
By default, it run a `xterm` app.

Run it.
`docker run --rm -d -p 8000:8000 -p 8088:8088 nediiii/novnc-continaer`
Visit [localhost:8000](localhost:8000) (or the ip of it) in your browser , which typicaly 

## How to dev

just do what ever you want.
There is nothing I hide.
