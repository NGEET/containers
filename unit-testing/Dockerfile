FROM ghcr.io/glemieux/containers/spack-env:latest

ARG CIME_VERSION=cime6.1.102

# Download and unpack CIME archive for tag cime6.1.102.  Rename the directory to cime.
RUN wget -q https://github.com/ESMCI/cime/archive/refs/tags/${CIME_VERSION}.tar.gz \
    && tar -xzf ${CIME_VERSION}.tar.gz \
    && mv cime-${CIME_VERSION} cime \
    && rm ${CIME_VERSION}.tar.gz

# Copy the cime configuration files in the .cime directory in the container
# COPY cime/ .cime/


