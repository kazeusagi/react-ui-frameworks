FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y \
  git \
  # sudo \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# non-root-userの追加
ARG USER_NAME=user
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USER_NAME \
  && useradd --uid $USER_UID --gid $USER_GID -m $USER_NAME -s /bin/bash
  # && echo $USER_NAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USER_NAME \
  # && chmod 0440 /etc/sudoers.d/$USER_NAME
USER $USER_NAME

# bunのインストール
RUN curl -fsSL https://bun.sh/install | bash
