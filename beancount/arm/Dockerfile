#FROM rukawa/alpine-arm-python:latest as builder
FROM python:3.6-alpine3.8 as builder

#COPY qemu-arm-static /usr/bin

RUN apk add --update libxml2-dev libxslt-dev gcc musl-dev g++
#RUN pip install -i https://mirrors.ustc.edu.cn/pypi/web/simple pip -U \
#    && pip config set global.index-url https://mirrors.ustc.edu.cn/pypi/web/simple
RUN pip install -U pip setuptools
RUN pip install --prefix="/install" fava

#FROM rukawa/alpine-arm-python:latest
FROM python:3.6-alpine3.8

COPY --from=builder /install /usr/local

ENV BEANCOUNT_FILE ""
ENV FAVA_OPTIONS ""
EXPOSE 5000
CMD fava --host 0.0.0.0 $FAVA_OPTIONS $BEANCOUNT_FILE