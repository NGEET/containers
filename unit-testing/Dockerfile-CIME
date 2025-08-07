FROM ghcr.io/ngeet/containers/spack-env:latest

ARG CIME_VERSION=cime6.1.102
ARG CCS_CONFIG_VERSION=ccs_config_cesm1.0.46

# Install wget
RUN apt-get update && apt-get install -y wget

# Download and unpack CIME archive for tag cime6.1.102.  Rename the directory to cime.
RUN wget -q https://github.com/ESMCI/cime/archive/refs/tags/${CIME_VERSION}.tar.gz \
    && tar -xzf ${CIME_VERSION}.tar.gz \
    && mv cime-${CIME_VERSION} cime \
    && rm ${CIME_VERSION}.tar.gz

RUN wget -q https://github.com/ESMCI/ccs_config_cesm/archive/refs/tags/${CCS_CONFIG_VERSION}.tar.gz \
    && tar -xzf ${CCS_CONFIG_VERSION}.tar.gz \
    && mv ccs_config_cesm-${CCS_CONFIG_VERSION} ccs_config \
    && rm ${CCS_CONFIG_VERSION}.tar.gz

# Copy the cime configuration files in the .cime directory in the container
COPY cime/ /root/.cime/

# Make sure that the entrypoint defined in the spack-env image is used
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/bin/bash" ]