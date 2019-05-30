FROM ubuntu AS builder
MAINTAINER b@akhras.at
WORKDIR /opt
RUN apt-get update -y && apt-get install -y git curl build-essential libfreetype6-dev
RUN git clone https://github.com/timvisee/pixelpwnr-server.git && curl -o /tmp/rust.sh https://sh.rustup.rs && sh /tmp/rust.sh -y
RUN cd pixelpwnr-server && source $HOME/.cargo/env && cargo build --release

FROM ubuntu
MAINTAINER b@akhras.at
WORKDIR /opt
COPY --from=builder /root/.cargo/bin/pixelpwnr-server .
COPY --from=builder /tmp/rust.sh .
RUN /tmp/rust.sh -y
CMD ["/opt/pixelpwnr-server"]




