FROM python:3.9

ENV PYTHONDONTWRITEBYTECODE 1

ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install python3 gcc libc-dev -y \
    && apt-get install -y binutils

RUN pip install --upgrade pip
COPY ./requirements.txt /requirements.txt
RUN  pip install -r /requirements.txt


RUN mkdir /app
WORKDIR /app
ENV SPRING_APPLICATION_NAME="account-service"
ENV SPRING_CLOUD_CONFIG_URI="http://service-config:8080"
ENV SPRING_CONFIG_IMPORT="configserver:http://service-config:8080"

COPY ./api /app

EXPOSE 8083

RUN sed -i 's/\r$//g' /app/start.sh
RUN chmod +x /app/start.sh


ENTRYPOINT [ "/app/start.sh" ]
