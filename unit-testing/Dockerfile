FROM ghcr.io/glemieux/containers/spack-env:latest

ARG CIME_VERSION=cime6.1.102

# Install wget
RUN apt-get update && apt-get install -y wget

# Download and unpack CIME archive for tag cime6.1.102.  Rename the directory to cime.
RUN wget -q https://github.com/ESMCI/cime/archive/refs/tags/${CIME_VERSION}.tar.gz \
    && tar -xzf ${CIME_VERSION}.tar.gz \
    && mv cime-${CIME_VERSION} cime \
    && rm ${CIME_VERSION}.tar.gz

# Copy the cime configuration files in the .cime directory in the container
# COPY cime/ .cime/

# # Install Python and pip
# RUN apt-get update && \
#     apt-get install -y python3 python3-pip && \
#     rm -rf /var/lib/apt/lists/*

# Make sure that the entrypoint defined in the spack-env image is used
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/bin/bash" ]