FROM python:3.8-slim-buster
WORKDIR /app
COPY requirements.txt /app
RUN python -m pip install -r requirements.txt
COPY . /app
EXPOSE 6666
CMD ["gunicorn", "--bind", "0.0.0.0:6666", "app:app"]
