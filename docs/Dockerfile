# since Sphinx >=5.0.0 is in requirements.txt, it automatically gets overwritten
# / downgraded when we build. That's an inefficient use of the image layers, so
# let's just start out with the 5.3.0 image.
ARG SPHINX_VERSION=5.3.0

FROM sphinxdoc/sphinx-latexpdf:${SPHINX_VERSION}

# LABEL org.opencontainers.image.authors = "Sphinx Team <https://www.sphinx-doc.org/>"
# LABEL org.opencontainers.image.documentation = "https://sphinx-doc.org/"
# LABEL org.opencontainers.image.source = "https://github.com/sphinx-doc/docker/"
# LABEL org.opencontainers.image.version = "5.3.0"
# LABEL org.opencontainers.image.licenses = "BSD-2-Clause"
# LABEL org.opencontainers.image.description = "Base container image for Sphinx"

WORKDIR /docs

# we need git so pip can install rinohtype from the github repo
RUN apt-get update \
    && apt-get install --no-install-recommends --yes \
    git \
    && apt-get autoremove \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ADD requirements.txt /docs
RUN python3 -m pip install --upgrade pip
RUN python3 -m pip install -r requirements.txt
