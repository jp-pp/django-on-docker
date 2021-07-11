# pull official base image
FROM python:3.9.5-alpine3.13

# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update \
    && apk add postgresql-dev gcc python3-dev musl-dev

RUN python -m pip install --upgrade pip
COPY ./requirements.txt .
RUN python -m pip install -r requirements.txt

# copy project
COPY . .

# copy entrypoint.sh
COPY ./entrypoint.sh .

## run entrypoint.sh
ENTRYPOINT ["/usr/src/app/entrypoint.sh"]