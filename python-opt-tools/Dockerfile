FROM ubuntu:18.04

# Installing Python 3.8 and PIP
RUN apt-get update && apt-get install -y python3.8
RUN apt-get install -y python3-pip

# Installing requirements
COPY requirements.txt /opt/requirements.txt
RUN pip3 install -r /opt/requirements.txt

WORKDIR /opt-tools

CMD ["/bin/bash"]