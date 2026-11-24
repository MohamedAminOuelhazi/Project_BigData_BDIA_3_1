FROM apache/hive:4.0.1

USER root

ENV HIVE_HOME=/opt/hive
ENV HADOOP_HOME=/opt/hadoop

# Ajouter la configuration personnalisée de Hive
COPY hive-site.xml /opt/hive/conf/hive-site.xml

# Préparer les répertoires utilisés par Hive
RUN mkdir -p /opt/hive/data/warehouse \
    /opt/hive/scratch_dir \
    /opt/hive/install_dir \
    && chown -R hive:root /opt/hive/data \
    /opt/hive/scratch_dir \
    /opt/hive/install_dir

WORKDIR /opt/hive

USER hive
