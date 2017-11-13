# Example of launch-function:
#
#function projectlibre {
#  if [ "$(docker ps -a -q -f name=projectlibre)" ]; then
#    docker container start projectlibre
#  else
#    docker run -it \
#      --net host \
#      -v /tmp/.X11-unix:/tmp/.X11-unix \
#      -e DISPLAY=unix$DISPLAY \
#      -v $HOME/Documents/projectlibre:/home/projectlibre \
#      --device /dev/snd \
#      --name projectlibre \
#      manofearth/projectlibre &
#  fi
#}b

FROM openjdk:latest

ADD https://downloads.sourceforge.net/project/projectlibre/ProjectLibre/1.7/projectlibre_1.7.0-1.deb /tmp/projectlibre_1.7.0-1.deb # considered as a bad practice, rewrite with curl or wget and combine with following two steps
RUN dpkg --install /tmp/projectlibre_1.7.0-1.deb
RUN rm /tmp/projectlibre_1.7.0-1.deb

RUN useradd projectlibre
USER projectlibre

ENTRYPOINT [ "projectlibre" ]
