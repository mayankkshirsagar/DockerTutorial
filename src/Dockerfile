FROM openjdk:21-jdk

WORKDIR /app

COPY Main.java .
# COPY instruction.txt .

RUN javac Main.java

CMD ["java", "Main"]
# CMD ["cat", "instruction.txt"]
