FROM mcr.microsoft.com/devcontainers/jekyll:2-bullseye

# Accept proxy settings as build arguments
ARG HTTP_PROXY=""
ARG HTTPS_PROXY=""
ARG NO_PROXY=""

# Set environment variables for proxy
ENV http_proxy=${HTTP_PROXY}
ENV https_proxy=${HTTPS_PROXY}
ENV HTTP_PROXY=${HTTP_PROXY}
ENV HTTPS_PROXY=${HTTPS_PROXY}
ENV no_proxy=${NO_PROXY}

# Configure apt to use proxy
RUN if [ -n "${HTTP_PROXY}" ]; then \
    echo "Acquire::http::Proxy \"${HTTP_PROXY}\";" >> /etc/apt/apt.conf.d/proxy.conf && \
    echo "Acquire::https::Proxy \"${HTTPS_PROXY}\";" >> /etc/apt/apt.conf.d/proxy.conf; \
    fi

# Install git lfs
RUN apt-get update -o APT::Acquire::Retries=3 && apt-get install -y \
    git-lfs \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Initialize git lfs
RUN git lfs install --system
