# Copyright 2018-2024 the Kubeapps contributors.
# SPDX-License-Identifier: Apache-2.0

# syntax = docker/dockerfile:1

FROM bitnami/golang:1.23.2 AS builder
WORKDIR /go/src/github.com/vmware-tanzu/kubeapps
COPY go.mod go.sum ./
COPY pkg pkg
COPY cmd cmd
ARG VERSION

# If true, run golangci-lint to detect issues
ARG lint

# https://github.com/golangci/golangci-lint/releases
ARG GOLANGCILINT_VERSION="1.61.0"

RUN if [ ! -z ${lint:-} ]; then \
  go install github.com/golangci/golangci-lint/cmd/golangci-lint@v$GOLANGCILINT_VERSION && \
  # Run golangci-lint to detect issues
  golangci-lint run --timeout=10m ./cmd/apprepository-controller/... && \
  golangci-lint run --timeout=10m ./pkg/... ; \
  fi

# With the trick below, Go's build cache is kept between builds.
# https://github.com/golang/go/issues/27719#issuecomment-514747274
RUN --mount=type=cache,target=/go/pkg/mod \
  --mount=type=cache,target=/root/.cache/go-build \
  GOPROXY="https://proxy.golang.org,direct" CGO_ENABLED=0 go build -installsuffix cgo -ldflags "-X github.com/vmware-tanzu/kubeapps/cmd/apprepository-controller/cmd.version=${VERSION:-}" ./cmd/apprepository-controller

FROM scratch
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=builder /go/src/github.com/vmware-tanzu/kubeapps/apprepository-controller /apprepository-controller
USER 1001
CMD ["/apprepository-controller"]
