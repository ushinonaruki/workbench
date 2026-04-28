FROM debian:bookworm-slim

ARG HOST_USER_ID
ARG HOST_GROUP_ID
ARG WORKBENCH_USER

# 取り込みフラグ
ARG INSTALL_FLG_NODE

# Node.js
ARG NODE_MAJOR
RUN if [ "${INSTALL_FLG_NODE}" = "true" ]; then \
      apt-get update; \
      apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        gnupg; \
      mkdir -p /etc/apt/keyrings; \
      curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key \
        | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg; \
      echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_${NODE_MAJOR}.x nodistro main" \
        > /etc/apt/sources.list.d/nodesource.list; \
      apt-get update; \
      apt-get install -y --no-install-recommends nodejs; \
      corepack enable || true; \
      node --version; \
      npm --version; \
      rm -rf /var/lib/apt/lists/*; \
    fi

RUN groupadd -g "${HOST_GROUP_ID}" "${WORKBENCH_USER}"
RUN useradd -m -u "${HOST_USER_ID}" -g "${HOST_GROUP_ID}" -s /bin/bash "${WORKBENCH_USER}"

WORKDIR /workspace

USER "${WORKBENCH_USER}"

CMD ["bash"]
