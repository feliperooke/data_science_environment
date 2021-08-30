FROM python:3.9.6

RUN pip install mlflow
RUN pip install psycopg2

EXPOSE 5000

RUN mkdir -p /server
WORKDIR /server
COPY wait-for-it.sh /server

RUN chmod +x wait-for-it.sh

RUN mkdir /mlflow/

CMD ./wait-for-it.sh postgres:5432 -s -- mlflow server \
    --backend-store-uri postgresql://admin:secret@postgres:5432/mlflow \
    --default-artifact-root /mlflow \
    --host 0.0.0.0