FROM tensorflow/tensorflow:2.2.0-gpu-jupyter

RUN pip install --upgrade pip

COPY requirements.txt /opt/requirements.txt
RUN pip install -r /opt/requirements.txt

