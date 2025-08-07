FROM ghcr.io/ngeet/containers/spack-env:latest

# Manually update the ctsm version here
ARG CTSM_VERSION=ctsm5.3.065

# Set runtime environment variables for branch name and URL
ENV BRANCH_NAME=""
ENV BRANCH_URL=""

# Install dependencies not associated with the spack environment
RUN apt-get update && apt-get install -y wget git python3

# Clone CTSM and checkout the specified version with git-fleximod
RUN git clone https://github.com/ESCOMP/CTSM.git && \
    cd CTSM && \
    git checkout ${CTSM_VERSION} && \
    ./bin/git-fleximod update

# Overwrite the container configuration files in ccs_config
COPY container/ /ctsm/ccs_config/container/

# Modify the .gitmodules file to take an environment variable from the container runtime command
RUN sed -i '/\[submodule "fates"\]/,/\[submodule /{s|^\(url *= *\).*|url = '"\${BRANCH_URL}"'|; s|^\(fxtag *= *\).*|fxtag = '"\${BRANCH_NAME}"'|}' /CTSM/.gitmodules

# Make sure that the entrypoint defined in the spack-env image is used
ENTRYPOINT [ "/entrypoint.sh" ]
CMD [ "/bin/bash" ]