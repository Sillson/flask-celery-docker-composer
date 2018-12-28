FROM python:3.6-alpine

ENV CELERY_BROKER_URL redis://redis:6379/0
ENV CELERY_RESULT_BACKEND redis://redis:6379/0
ENV C_FORCE_ROOT true

ENV HOST 0.0.0.0
ENV PORT 5000
ENV DEBUG true

ADD . /my_test_app
WORKDIR /my_test_app

# install requirements
RUN pip install --upgrade pip && \
    pip install -r my_test_app/requirements.txt
    #pip install -r requirements.txt

# expose the app port
EXPOSE 5000

RUN pip install gunicorn

# run the app server
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "--log-level=DEBUG", "--workers", "3", "my_test_app:app", "--reload"]
