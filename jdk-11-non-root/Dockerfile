FROM adoptopenjdk/openjdk11:alpine-jre

ENV USER=docker
ENV UID=1001
ENV GID=2001

RUN addgroup \
  --gid "${GID}" \
  "${USER}"
RUN adduser \
  --disabled-password \
  --gecos "" \
  --home "$(pwd)" \
  --ingroup "${USER}" \
  --no-create-home \
  --uid "$UID" \
  "${USER}"

USER ${USER}
