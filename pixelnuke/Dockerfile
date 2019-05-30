FROM ubuntu AS builder
MAINTAINER b@akhras.at
WORKDIR /opt
RUN apt-get update -y && apt-get install -y build-essential libevent-dev libglew-dev libglfw3-dev git
RUN git clone https://github.com/defnull/pixelflut && cd pixelflut/pixelnuke && make

FROM ubuntu
MAINTAINER b@akhras.at
WORKDIR /opt
RUN apt-get update -y
RUN apt-get install -y libevent-dev libglew-dev libglfw3-dev
COPY --from=builder /opt/pixelflut/pixelnuke .
CMD ["/opt/pixelnuke"]




