FROM debian:9.6

ENV JRE_BUILD 12
ENV JRE_PATCH 191
ENV JRE_VERSION 1.8.0_${JRE_PATCH}
ENV JRE_PATH_ID 2787e4a523244c269598db4e85c51e0c

ENV JAVA_HOME /usr/lib/jvm/jdk${JRE_VERSION}

RUN mkdir /usr/lib/jvm

RUN apt-get update \
    && apt-get install -y curl \
    && curl -s -L -b "oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u${JRE_PATCH}-b${JRE_BUILD}/${JRE_PATH_ID}/server-jre-8u${JRE_PATCH}-linux-x64.tar.gz | tar -C /usr/lib/jvm -xzf - \
    && apt-get purge -y curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN update-alternatives --install /usr/bin/java java ${JAVA_HOME}/bin/java 100 && \
	update-alternatives --set java ${JAVA_HOME}/bin/java

RUN update-alternatives --install /usr/bin/javac javac ${JAVA_HOME}/bin/javac 100 && \
	update-alternatives --set javac ${JAVA_HOME}/bin/javac

RUN update-alternatives --install /usr/bin/jar jar ${JAVA_HOME}/bin/jar 100 && \
	update-alternatives --set jar ${JAVA_HOME}/bin/jar
