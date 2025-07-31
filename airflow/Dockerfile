FROM apache/airflow:2.3.0-python3.8
LABEL org.opencontainers.image.source=https://github.com/maastrichtlawtech/case-law-explorer
USER root
RUN apt-get update && apt-get install -y gcc python3-dev && apt-get autoremove -yqq --purge && apt-get clean
USER airflow 
RUN mkdir -p /opt/airflow/data/raw
RUN mkdir -p /opt/airflow/data/processed
COPY ./requirements.txt ./requirements.txt
RUN python3 -m pip install --upgrade pip
RUN pip3 install -r ./requirements.txt
RUN pip3 uninstall -y argparse
RUN ln -sf /usr/share/zoneinfo/Europe/Amsterdam/etc/localtime
CMD 'airflow db init'
ENV TZ=Europe/Warsaw
