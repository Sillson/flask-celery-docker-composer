FROM python:3.6-alpine


ENV CELERY_BROKER_URL redis://redis:6379/0
ENV CELERY_RESULT_BACKEND redis://redis:6379/0
ENV C_FORCE_ROOT true

COPY ./celery_queue /queue
COPY ./my_test_app/jobs /queue/.
COPY ./my_test_app/config /queue/config
WORKDIR /queue

RUN pip install -r requirements.txt

ENTRYPOINT celery -A tasks worker --loglevel=info
