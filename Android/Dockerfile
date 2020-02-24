FROM ubuntu:16.04

ARG ANDROID_SDK_VERSION=r24.4.1
ARG GRADLE_VERSION=6.1.1

RUN apt-get update \
  && apt-get -y install sudo \
  && useradd -m docker && echo "docker:docker" | chpasswd && adduser docker sudo

# Install 32bit lib
RUN sudo apt-get -y install lib32stdc++6 lib32z1

# Install Java8
RUN apt-get install -y software-properties-common curl \
    && add-apt-repository -y ppa:openjdk-r/ppa \
    && apt-get update \
    && apt-get install -y openjdk-8-jdk

# Download Android SDK & gradle
RUN sudo apt-get -y install wget unzip \
    && cd /usr/local \
    && wget http://dl.google.com/android/android-sdk_${ANDROID_SDK_VERSION}-linux.tgz \
    && tar zxvf android-sdk_${ANDROID_SDK_VERSION}-linux.tgz \
    && rm -rf /usr/local/android-sdk_${ANDROID_SDK_VERSION}-linux.tgz \
    && cd /usr/lib \
    && wget https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip \
    && unzip gradle-${GRADLE_VERSION}-bin.zip \
    && ln -s /usr/gradle-${GRADLE_VERSION}/bin/gradle /usr/bin/gradle \
    && rm gradle-${GRADLE_VERSION}-bin.zip

# Environment variables
ENV GRADLE_HOME /usr/lib/gradle-$GRADLE_VERSION
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64
ENV ANDROID_HOME /usr/local/android-sdk-linux
ENV PATH $ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH $PATH:$GRADLE_HOME/bin

# Update of Android SDK
RUN echo y | android update sdk --no-ui --all --filter "android-28,build-tools-28.0.2" \
  && echo y | android update sdk --no-ui --all --filter "extra-google-m2repository,extra-android-m2repository"
