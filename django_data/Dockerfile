FROM python:3.6
WORKDIR /code
ENV PYTHONUNBUFFERED 1
COPY requirements.txt /code/
RUN mkdir /code/media && \
    mkdir /code/static &&\
    python -m pip install --upgrade pip &&\
    pip install -r requirements.txt
COPY . /code/