FROM openjdk:11
WORKDIR /usr/src/
COPY Main.java .
RUN javac Main.java
Run pwd && ls

FROM openjdk:11-jre
WORKDIR /usr/src/
COPY --from=0 /usr/src/Main.class .
RUN java Main
