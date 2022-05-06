ARG HTTP_PROXY=${HTTP_PROXY}
FROM python:3.9.9

ENV HTTP_PROXY=${HTTP_PROXY} \
    HTTPS_PROXY=${HTTP_PROXY} \
    http_proxy=${HTTP_PROXY} \
    https_proxy=${HTTP_PROXY} \
    NO_PROXY=localhost,127.0.0.1 \
    no_proxy=localhost,127.0.0.1

RUN apt-get update
RUN apt-get install -y ca-certificates fonts-ipafont \
 && update-ca-certificates

RUN set -eux && \
    python -m pip install --upgrade pip && \
    python -m pip install sphinx sphinx-autobuild rstcheck sphinxcontrib-blockdiag sphinxcontrib-blockdiag sphinxcontrib-seqdiag sphinxcontrib-actdiag sphinxcontrib-nwdiag sphinx-copybutton

RUN curl -k https://raw.githubusercontent.com/thoughtworks/talisman/master/global_install_scripts/install.bash > /tmp/install_talisman.bash && chmod a+x /tmp/install_talisman.bash

RUN set -eux && \
    mkdir -p /workspace

WORKDIR /workspace/oase-docs