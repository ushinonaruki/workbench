FROM debian:bookworm-slim

ARG HOST_USER_ID
ARG HOST_GROUP_ID
ARG WORKBENCH_USER

RUN groupadd -g "${HOST_GROUP_ID}" "${WORKBENCH_USER}"
RUN useradd -m -u "${HOST_USER_ID}" -g "${HOST_GROUP_ID}" -s /bin/bash "${WORKBENCH_USER}"

WORKDIR /workspace

USER "${WORKBENCH_USER}"

CMD ["bash"]
