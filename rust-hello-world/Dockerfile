FROM rust as builder
RUN mkdir /src
WORKDIR /src
COPY . .
RUN cargo build --release

FROM alpine
RUN apk add --no-cache libgcc gcompat
WORKDIR /root
COPY --from=builder /src/target/release/hello-world .
CMD ["./hello-world"]