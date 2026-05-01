# VectorVoyage
VectorVoyage is a solution for querying datasets with 100% efficiency using Elasticsearch. During document ingestion, we dynamically generate an array of the most relevant keywords from each document. This array is then converted into a vector and appended to the document before it is indexed in Elasticsearch.


## Key Technologies:

Elasticsearch: For efficient data querying.
FastAPI: A modern, fast (high-performance) web framework for building APIs with Python 3.7+ based on standard Python type hints.
React: A JavaScript library for building user interfaces, primarily used here in TypeScript to create a responsive and interactive front-end.


![VectorVoyage app screenshot](screenshot.png)

## What is this?

This repository contains a small application that demonstrates how easy it is
to set up a vector database using [Elasticsearch](https://www.elastic.co/elasticsearch)
and the [Elasticsearch-DSL](https://elasticsearch-dsl.readthedocs.io/) client
for Python.

The application includes a FastAPI back end and a React front end written in
TypeScript. The data is stored in an Elasticsearch index, and for each document
an embedding is generated using the
[all-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
Sentence Transformers model.

## Requirements

Please make sure you have the following installed:

- Python 3.10 or newer
- Node.js 18 or newer
- Docker

## How To Run

Follow these steps to install this demo on your computer:

### Clone this repository

Run the following command to install a copy of this project on your computer:

```bash
git clone https://github.com/santenova/VectorVoyage.git
cd VectorVoyage
```

### Install the Node and Python dependencies

Run the following command to set up the JavaScript and Python environment and
install all the dependencies:

```bash
npm install
```

### Elasticsearch

Start a development Elasticsearch container via docker should you not have
a running instance

Run this command to start a single-node Elasticsearch instance:

```bash
docker run -p 9200:9200 -d --name elasticsearch \
  -e "discovery.type=single-node" \
  -e "xpack.security.enabled=false" \
  -e "xpack.security.http.ssl.enabled=false" \
  -e "xpack.license.self_generated.type=basic" \
  -v "./backend/data:/usr/share/elasticsearch/data" \
  docker.elastic.co/elasticsearch/elasticsearch:8.15.0
```

### Create the quotes database

Run this command in your terminal:

```bash
npm run ingest
```

Note that depending on your computer speed and wether you have a GPU or not this
may take a few minutes.

### Start the back end

Run this command in your terminal:

```bash
npm run backend
```

### Start the front end

Open a second terminal window and run this command:

```bash
npm start
```

You can now navigate to `http://localhost:3000` on your web browser to access
the application.
