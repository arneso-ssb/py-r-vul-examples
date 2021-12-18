# This dockerfile creates a python container with a security vulnerability.
FROM python:3.9-slim

COPY requirements.txt .

RUN pip install -r requirements.txt && rm requirements.txt
