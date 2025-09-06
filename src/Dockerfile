# load the base docker image / VM , for our java program we will load java 21 image
FROM openjdk:21-jdk

# create workdir in docker, this will be working directory in our docker space
WORKDIR /app
# CMD ["pwd"] -> /app

# copy only the java main file
COPY Main.java .
# COPY . .   -> this copies everything in the dockerfile directory, we can use dockerignore file to ignore similar to git ignore
# COPY instruction.txt . -> copy instruction.txt to docker

RUN javac Main.java

# only one CMD command can run in a stage, if multiple are added only last one will run
# CMD ["pwd"]
# CMD ["java", "Main"]
# CMD ["cat", "instruction.txt"]
# CMD ["cat", "testignore.txt"] -> cat: testignore.txt: No such file or directory -> if this file is added to dockerignore
