FROM julia:1.5.2

RUN mkdir -p /Code
RUN mkdir -p /Code/julia

WORKDIR /Code/julia
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get install -y git && apt-get clean && \
    git clone https://github.com/huanglangwen/JlBox.git

RUN julia --eval 'using Pkg;Pkg.develop(PackageSpec(path="/Code/julia/JlBox"));Pkg.build("JlBox")'

WORKDIR /Code/julia/JlBox
RUN julia example/Install_package.jl
