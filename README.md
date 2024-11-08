# Projeto conversao-distancia em Container Docker

## Dockerfile para criação da imagem customizada

FROM python
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . /app/
EXPOSE 5000
CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]

## Criando a imagem docker
docker build -t conversao-distancia -f Dockerfile .

## Criando o container docker
docker container run -d -p 8181:5000 conversao-distancia