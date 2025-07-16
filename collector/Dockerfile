FROM public.ecr.aws/docker/library/golang:1.24 AS collector-builder
WORKDIR /src
COPY . .
RUN go mod tidy
RUN GO111MODULE=on CGO_ENABLED=0 installsuffix=cgo go build -trimpath -o collector .

FROM scratch
COPY --from=collector-builder /src/collector src/collector