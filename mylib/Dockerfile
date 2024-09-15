FROM ghcr.io/astral-sh/uv:python3.12-bookworm AS builder
WORKDIR /mylib
COPY . /mylib/
RUN --mount=type=cache,target=/root/.cache/uv \
    uv build

FROM python:3.12-slim-bookworm
RUN --mount=type=bind,from=builder,source=/mylib/dist,target=/packages \
    pip install /packages/*.whl
CMD ["python", "-m", "mylib"]
