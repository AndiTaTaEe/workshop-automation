FROM ubuntu:24.04 as builder
RUN apt-get update && apt-get install -y gcc
WORKDIR /build
COPY bye.c .
# compile statically so the binary doesn't depend on external libraries
RUN gcc bye.c -o program_bye -static

# final runtime environment - contains only the executable
FROM alpine:latest
WORKDIR /app
COPY --from=builder /build/program_bye .
CMD ["./program_bye"]