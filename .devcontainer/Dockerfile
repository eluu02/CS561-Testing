# Use Debian slim as base
FROM debian:bullseye-slim

# Environment variables
ENV DEBIAN_FRONTEND=noninteractive
ENV QUICKLISP_DIR=/root/.quicklisp

# Install prerequisites
RUN apt-get update && apt-get install -y \
    curl \
    build-essential \
    sbcl \
    unzip \
    git \
    && rm -rf /var/lib/apt/lists/*

# Install Quicklisp
RUN curl -O https://beta.quicklisp.org/quicklisp.lisp && \
    sbcl --non-interactive --load quicklisp.lisp \
        --eval "(quicklisp-quickstart:install :path \"$QUICKLISP_DIR\")" \
        --quit && \
    rm quicklisp.lisp && \
    echo "(load \"$QUICKLISP_DIR/setup.lisp\")" >> /root/.sbclrc