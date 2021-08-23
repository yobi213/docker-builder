FROM pytorchlightning/pytorch_lightning:base-conda-py3.8-torch1.7

RUN apt-get update && apt-get install -y --no-install-recommends apt-utils
RUN buildDeps='gcc libc6-dev make build-essential curl gnupg' \
    && apt-get update && apt-get install -y $buildDeps git wget tar \
    && pip install --upgrade pip \
    && apt-get install unzip
RUN wget https://download.oracle.com/otn_software/linux/instantclient/213000/instantclient-basic-linux.x64-21.3.0.0.0.zip
RUN unzip instantclient-basic-linux.x64-21.3.0.0.0.zip -d /opt/oracle
RUN echo "export PATH="$PATH:/opt/oracle/instantclient_21_3/"" >> ~/.bashrc

COPY requirements.txt .
RUN pip install -r requirements.txt

CMD ["sh","-c", "jupyter lab --ip=0.0.0.0 --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*'"]
