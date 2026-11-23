#FROM python:3.12-slim
#WORKDIR /app
#ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1
#COPY requirements.txt ./
#RUN pip install --no-cache-dir -r requirements.txt fastapi
#COPY main.py ./
#EXPOSE 8000
#CMD ["python", "-m", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]


## VERSIONE PROF. Menapace

#FROM python:3.12-slim
#WORKDIR /app
#COPY requirements.txt ./
#RUN pip install --no-cache-dir -r requirements.txt fastapi
#COPY main.py ./
#ENTRYPOINT ["python", "-m", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]


# VERSIONE Con clone del repo
FROM python:3.12-slim

RUN apt-get update \
    && apt-get install -y --no-install-recommends git \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

RUN git clone https://github.com/mmenapace/SomeBankingApp.git .

WORKDIR /app/backend

RUN pip install --no-cache-dir -r requirements.txt fastapi

EXPOSE 8000

ENTRYPOINT ["python", "-m", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]

#avvio backend: docker run -d --name banking-backend -p 8000:8000 banking-backend:1.0