FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive 
RUN apt-get update && apt-mark hold linux-image-generic linux-headers-generic
RUN apt-get install -y build-essential git gfortran \
 && apt-get clean
 
RUN mkdir -p /Code
WORKDIR /Code
RUN git clone https://github.com/huanglangwen/kpp_APINENE.git --branch v0.1

WORKDIR /Code/kpp_APINENE
RUN make
CMD ["/Code/kpp_APINENE/mcm_subset2.exe"]

