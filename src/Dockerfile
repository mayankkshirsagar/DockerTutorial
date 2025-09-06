# load the base docker image / VM , for our java program we will load java 21 image
# stage 1
FROM eclipse-temurin:17-jdk AS builder

# if we need to pass arguments in the build command : docker build --build-arg DATE="5-10-15"  -t java-hello-world-custom-tag .
ARG DATE

# create workdir in docker, this will be working directory in our docker space
WORKDIR /app
# CMD ["pwd"] -> /app

# copy only the java main file
COPY Main.java .
# COPY . .   -> this copies everything in the dockerfile directory, we can use dockerignore file to ignore similar to git ignore
# COPY instruction.txt . -> copy instruction.txt to docker

# ADD DOCKER_BUILDKIT=0  in build command to see the echo output during build
# DOCKER_BUILDKIT=0 docker build --build-arg DATE="5-10-15" -t java-hello-world-custom-tag .
RUN echo "DATE IS ${DATE}"

RUN javac Main.java

# multi stage docker file used to get smaller images with only minimal requirements, which helps reducing size
# in this example we are using entire jdk image to run the java program vs in the multistage we first create class using JDK but only run using JRE which is much smaller in size
# each stage is a separate image, and Docker only uses the final one to produce the final result.
# first build this image and see the size of the image (image size = 600 mb due to jdk)
# next uncomment the below 2 lines and build and see the size of the image (image size = 300 mb due to jre)

# stage 2
FROM eclipse-temurin:17-jre-focal AS server
COPY --from=builder /app/Main.class .

# only one CMD command can run in a stage, if multiple are added only last one will run
# CMD ["pwd"]
CMD ["java", "Main"]
# CMD ["cat", "instruction.txt"]
# CMD ["cat", "testignore.txt"] -> cat: testignore.txt: No such file or directory -> if this file is added to dockerignore
