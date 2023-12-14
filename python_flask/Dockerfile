

FROM python:3-alpine3.15

WORKDIR /app

COPY . /app

RUN pip install -r requirements.txt
RUN pip install gunicorn

EXPOSE 5000

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "index:app"]
