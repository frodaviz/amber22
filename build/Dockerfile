#FROM nvidia/cuda:11.6.1-devel-ubuntu20.04
FROM nvidia/cuda:11.8.0-devel-ubuntu20.04
#FROM nvidia/cuda:12.2.2-base-ubuntu20.04 # con questo non builda

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get install -y apt-utils tzdata && \
    apt-get upgrade -y && \
    apt-get install -y csh flex bison patch gcc gfortran g++ make \
                       build-essential xorg-dev xutils-dev libbz2-dev zlib1g-dev \
                       libboost-dev libboost-thread-dev libboost-system-dev mpich libmpich-dev \
                       python3 wget bc cmake git gromacs doxygen libfftw3-dev automake lsb-core

ENV PATH="${PATH}:/opt/miniconda/bin:${PATH}"

USER root

ADD tars /opt/

RUN wget https://repo.continuum.io/miniconda/Miniconda3-4.5.11-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p "/opt/miniconda" && \
    rm -f miniconda.sh && \
    mkdir /.conda &&  chmod -R 777 /.conda &&  chmod -R 777 /opt/miniconda && \
    conda install -y cmake numpy scipy pytest swig cython && \
    rm -rf /opt/amber22_src

WORKDIR /opt/

RUN tar xvfj Amber22.tar.bz2 && \
    tar xvfj AmberTools23.tar.bz2 && \
    mkdir -p /opt/amber22_src/build/ && \
    mkdir -p /work

WORKDIR /opt/amber22_src/build/

COPY run_cmake /opt/amber22_src/build/

RUN pwd && \
    ls -altr && \
    cat /opt/amber22_src/build/run_cmake && \
    bash "/opt/amber22_src/build/run_cmake" && \
    make install

WORKDIR /work

