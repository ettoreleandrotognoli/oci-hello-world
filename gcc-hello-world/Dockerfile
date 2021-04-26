FROM gcc as builder
RUN mkdir /src
WORKDIR /src
COPY . .
RUN gcc hello_world.c -o run.o

FROM alpine
RUN apk add --no-cache libgcc gcompat
WORKDIR /root
COPY --from=builder ./src/run.o .
CMD ./run.o