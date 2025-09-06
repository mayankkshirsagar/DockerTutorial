FROM openjdk:21-jdk

WORKDIR /app

# copy only the java man file
COPY Main.java .
# COPY . .   -> this copies everything in the dockerfile directory, we can use dockerignore file to ignore similar to git ignore
# COPY instruction.txt . -> copy instruction.txt to docker

RUN javac Main.java

# only one CMD command can run in a stage, if multiple are added only last one will run
CMD ["java", "Main"]
# CMD ["cat", "instruction.txt"]
# CMD ["cat", "testignore.txt"] -> cat: testignore.txt: No such file or directory -> if this file is added to dockerignore
