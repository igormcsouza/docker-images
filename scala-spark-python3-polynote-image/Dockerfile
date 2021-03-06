FROM ubuntu:18.04

RUN apt-get update

# Install Java
RUN apt-get install -y openjdk-8-jdk
ENV JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/

# Install Scala
RUN apt-get update && apt-get install -y scala
ENV SPARK_HOME=/packages/spark-2.4.5-bin-hadoop2.7/

# Install Python
RUN apt-get update && apt-get install -y python3.7 && apt install -y python3-pip

# Install others depedencies
RUN apt-get install -y wget

WORKDIR /packages

# Installing Polynote, the polyglot Jupyter Notebook
RUN wget https://github.com/polynote/polynote/releases/download/0.3.3/polynote-dist.tar.gz
RUN tar -zxvpf polynote-dist.tar.gz

# Install Spark + Hadoop
RUN wget http://ftp.unicamp.br/pub/apache/spark/spark-2.4.5/spark-2.4.5-bin-hadoop2.7.tgz
RUN tar -zxvf spark-2.4.5-bin-hadoop2.7.tgz

ENV PATH="$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin"

RUN pip3 install jep jedi pyspark

# Install Jupiter Notebook + Scala kernel
RUN pip3 install notebook spylon-kernel
RUN python3 -m spylon_kernel install

# Install git
RUN apt update && apt install -y git

# Install extra packages as required
COPY requirements.txt /opt/requirements.txt
RUN pip3 install -r /opt/requirements.txt

# Expose the needed ports
EXPOSE 8192
EXPOSE 8888

WORKDIR /workdir

CMD [ "ipython", "notebook", "--allow-root" ]
# CMD [ "/bin/bash" ]
