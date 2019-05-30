To build:

docker build . -t x/pixelnuke


To run:

docker run docker run --name pixler --rm -it -p 1337:1337 --env="DISPLAY" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" x/pixelnuke
 
