FROM tensorflow/tensorflow:2.0.1-gpu-py3-jupyter

RUN pip install --upgrade pip

COPY requirements.txt /opt/requirements.txt
RUN pip install -r /opt/requirements.txt

