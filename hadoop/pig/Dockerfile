FROM eclipse-temurin:11-jre

ENV HADOOP_VERSION=3.4.1
ENV PIG_VERSION=0.18.0

ENV JAVA_HOME=/opt/java/openjdk
ENV HADOOP_HOME=/opt/hadoop
ENV PIG_HOME=/opt/pig

ENV PATH=${PATH}:${HADOOP_HOME}/bin:${PIG_HOME}/bin

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    tar \
    gzip \
    python3 \
    && rm -rf /var/lib/apt/lists/*

# Install Hadoop client
RUN wget -q https://archive.apache.org/dist/hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz \
    -O /tmp/hadoop.tar.gz \
    && tar -xzf /tmp/hadoop.tar.gz -C /opt \
    && mv /opt/hadoop-${HADOOP_VERSION} ${HADOOP_HOME} \
    && rm /tmp/hadoop.tar.gz

# Install Apache Pig
RUN wget -q https://archive.apache.org/dist/pig/pig-${PIG_VERSION}/pig-${PIG_VERSION}.tar.gz \
    -O /tmp/pig.tar.gz \
    && tar -xzf /tmp/pig.tar.gz -C /opt \
    && mv /opt/pig-${PIG_VERSION} ${PIG_HOME} \
    && rm /tmp/pig.tar.gz

ENV HADOOP_CONF_DIR=${HADOOP_HOME}/etc/hadoop

WORKDIR /workspace

CMD ["tail", "-f", "/dev/null"]
