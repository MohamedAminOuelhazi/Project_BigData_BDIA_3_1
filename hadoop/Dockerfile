
FROM eclipse-temurin:11-jre-jammy

RUN apt-get update && \
    apt-get install -y --no-install-recommends curl procps && \
    rm -rf /var/lib/apt/lists/*

ENV HADOOP_VERSION=3.4.1
ENV HADOOP_HOME=/opt/hadoop
ENV JAVA_HOME=/opt/java/openjdk
ENV PATH="${HADOOP_HOME}/bin:${HADOOP_HOME}/sbin:${PATH}"

RUN curl -fSL \
    "https://archive.apache.org/dist/hadoop/common/hadoop-${HADOOP_VERSION}/hadoop-${HADOOP_VERSION}.tar.gz" \
    -o /tmp/hadoop.tar.gz && \
    tar -xzf /tmp/hadoop.tar.gz -C /opt && \
    ln -s "/opt/hadoop-${HADOOP_VERSION}" "${HADOOP_HOME}" && \
    rm /tmp/hadoop.tar.gz

COPY config/ ${HADOOP_HOME}/etc/hadoop/

RUN useradd -m -u 1000 hadoop && \
    mkdir -p /hadoop/dfs/name /hadoop/dfs/data && \
    chown -R hadoop:hadoop /opt/hadoop-${HADOOP_VERSION} \
        /hadoop

USER hadoop

WORKDIR /home/hadoop

CMD ["bash"]
