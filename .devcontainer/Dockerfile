FROM python:3.8-slim-buster

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    curl wget gosu jq unzip libgomp1 default-libmysqlclient-dev python3-dev

RUN apt-get install -y g++ cmake make

RUN cd /tmp \
  && wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz \
  && tar -xvf ta-lib-0.4.0-src.tar.gz \
  && cd ta-lib \
  && ./configure --prefix=/usr \
  && (make -j4 || make) \
  && make install \
  && rm -rf /tmp/*

COPY requirements.txt /tmp/
RUN pip install --upgrade pip && \
    pip install -r /tmp/requirements.txt