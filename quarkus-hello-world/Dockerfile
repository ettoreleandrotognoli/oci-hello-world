FROM ghcr.io/graalvm/graalvm-ce:latest as builder
RUN gu install native-image
RUN mkdir /src
WORKDIR /src
COPY . .
RUN ./mvnw -Pnative package

FROM alpine
RUN apk add --no-cache libgcc gcompat
WORKDIR /root
COPY --from=builder /src/target/*-runner main
CMD ["./main"]
