FROM ubuntu:20.04

# Install the packages required to compile mrtrix3
RUN apt-get update && DEBIAN_FRONTEND="noninteractive" apt-get install git g++ python-is-python3 libeigen3-dev zlib1g-dev libqt5opengl5-dev libqt5svg5-dev libgl1-mesa-dev libfftw3-dev libtiff5-dev libpng-dev -y

# Compile mrtrix
RUN git clone --depth 1 --branch 3.0.2 https://github.com/MRtrix3/mrtrix3.git
RUN cd mrtrix3 && ./configure && ./build

# Copy files to make them callable from everywhere
RUN cp -R /mrtrix3/bin/* /usr/bin/
RUN cp -R /mrtrix3/lib/* /usr/lib/

# Clean-up
RUN rm -R /mrtrix3/

