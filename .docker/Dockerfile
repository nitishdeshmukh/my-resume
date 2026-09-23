ARG PLATFORM=linux/amd64
FROM --platform=${PLATFORM} debian:bookworm-slim

ENV PATH="/root/.TinyTeX/bin/x86_64-linux:${PATH}"

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      wget xz-utils perl ca-certificates fontconfig && \
    rm -rf /var/lib/apt/lists/* && \
    wget -qO- "https://yihui.org/tinytex/install-bin-unix.sh" | sh && \
    tlmgr install \
      enumitem titlesec xcharter xcharter-math fontaxes mweights carlisle etoolbox \
      xstring geometry fancyhdr xkeyval microtype hyperxmp \
      datetime2 datetime2-english embedfile ly1 && \
    tlmgr path add && \
    test -f /root/.TinyTeX/texmf-dist/tex/latex/xcharter/XCharter.sty

WORKDIR /data
ENTRYPOINT ["pdflatex"]
