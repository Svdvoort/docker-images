FROM ubuntu:20.04

# Prepare system packages
RUN apt-get update
# wget is need to get Elastix package
# libgomp1 is required by elastix
RUN apt-get -qq install wget libgomp1 -y

# Get elastix 5.0.1
RUN wget -q https://www.github.com/SuperElastix/elastix/releases/download/5.0.1/elastix-5.0.1-linux.tar.bz2
# Extract the files
RUN tar -xjf elastix-5.0.1-linux.tar.bz2

# Copy bins and libraries to general use location
RUN cp elastix-5.0.1-linux/bin/* /usr/local/bin/
RUN cp elastix-5.0.1-linux/lib/* /usr/lib/

# Copy license and notice
RUN cp elastix-5.0.1-linux/LICENSE /
RUN cp elastix-5.0.1-linux/NOTICE /

# Clean-up
RUN rm elastix-5.0.1-linux.tar.bz2
RUN rm -r elastix-5.0.1-linux/
