FROM debian:8

ENV JDK_BUILD 15
ENV JDK_PATCH 72
ENV JDK_VERSION 1.8.0_${JDK_PATCH}

ENV JAVA_HOME /usr/lib/jvm/jdk${JDK_VERSION}

RUN mkdir /usr/lib/jvm

RUN apt-get update \
    && apt-get install -y curl \
    && curl -s -L -b "oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u${JDK_PATCH}-b${JDK_BUILD}/jdk-8u${JDK_PATCH}-linux-x64.tar.gz | tar -C /usr/lib/jvm -xzf - \
    && apt-get purge -y curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
  

RUN update-alternatives --install /usr/bin/java java ${JAVA_HOME}/bin/java 100 && \
	update-alternatives --set java ${JAVA_HOME}/bin/java

RUN update-alternatives --install /usr/bin/javac javac ${JAVA_HOME}/bin/javac 100 && \
	update-alternatives --set javac ${JAVA_HOME}/bin/javac

RUN update-alternatives --install /usr/bin/jar jar ${JAVA_HOME}/bin/jar 100 && \
	update-alternatives --set jar ${JAVA_HOME}/bin/jar

ENTRYPOINT ["java"]
