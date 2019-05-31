FROM ubuntu AS builder
MAINTAINER b@akhras.at
WORKDIR /opt
RUN apt-get update -y && apt-get install -y git curl build-essential libfreetype6-dev
RUN git clone https://github.com/timvisee/pixelpwnr-server.git && curl -o /opt/rust.sh https://sh.rustup.rs && sh /opt/rust.sh -y
RUN . $HOME/.cargo/env && cd pixelpwnr-server && cargo build --release

FROM ubuntu
MAINTAINER b@akhras.at
WORKDIR /opt
COPY --from=builder /opt/pixelpwnr-server/target/release/pixelpwnr-server .
COPY --from=builder /opt/rust.sh .
RUN apt-get update -y && apt-get install -y curl
RUN /bin/sh /opt/rust.sh -y
CMD ["/opt/pixelpwnr-server"]

