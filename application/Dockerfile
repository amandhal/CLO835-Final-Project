FROM ubuntu:20.04
RUN apt-get update -y && apt install iputils-ping -y
COPY . /app
WORKDIR /app
RUN set -xe \
    && apt-get update -y \
    && apt-get install -y python3-pip \
    && apt install -y vim \
    && apt install -y curl \
    && apt-get install -y mysql-client 
RUN pip install --upgrade pip
RUN pip install boto3
RUN mkdir /app/static
RUN pip install -r requirements.txt
EXPOSE 81
ENTRYPOINT [ "python3" ]
CMD [ "app.py" ]
