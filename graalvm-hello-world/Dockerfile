FROM ghcr.io/graalvm/graalvm-ce:latest as builder
RUN gu install native-image
RUN mkdir /src
WORKDIR /src
COPY . .
RUN javac Main.java
RUN native-image Main

FROM alpine
RUN apk add --no-cache libgcc gcompat
WORKDIR /root
COPY --from=builder /src/main .
CMD ["./main"]