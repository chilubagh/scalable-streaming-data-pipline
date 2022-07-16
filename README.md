

## Introduction

Data streaming is part of a data engineers job.In this project, I am going to build a very simple and highly scalable data streaming pipeline using Python. Data streaming is the process of transmitting a continuous flow of data.

![Data pipline](https://user-images.githubusercontent.com/51442225/179332300-80b9eb84-30c7-475d-96eb-459b7a13ee5b.png)

One side of the pipeline would have some or at least one data producer who would be continuously producing data and on the other side, we would have some or at least one data consumer who would be consuming that data continuously.

## Architecture

![Pipeline architecture](https://miro.medium.com/max/1400/1*9m4bX85qMH3jAeimuDR_kQ.png)

I will be using Redis as data pipeline and using a very simple data scraping microservice using Scrapy independently as a data producer and a separate microservice as a data consumer.

## Installation
Install the Redis and run it locally.

Clone the repository.
 `git clone git@github.com:chilubagh/scalable-streaming-data-pipline.git`

Install the requirements.

`pip install -r requirements.txt`
You are good to go!

Quick start

`Start the producer quotes_spider`:

`cd producer`

scrapy crawl quotes
Start the consumer quotes_consumer:

`cd consumer`

python quotes_consumer.py

## Building the data Producer

I am building a simple python project with scrapy in a virtual environment.
I run the command given below to create an empty Scrapy project.

`scrapy startproject producer`

Our data producer side is ready now but we need to put that data into a data pipeline instead of in a file. Before putting data into a data pipeline we need to build a data pipeline before.

## The redis pipeline

Redis was installed and made to run

<img width="1425" alt="Screenshot 2022-07-16 at 23 34 57" src="https://user-images.githubusercontent.com/51442225/179371178-21e0ad6b-812b-47dc-8f56-a1139fcd1ce1.png">

Wrappers are created around Redis functions to make them more humane. Let’s start with creating a directory in root with a name pipeline and create a new file **redis_client.py**.This client implements FIFO for the pipeline.

## Ingestion of data from the producer

With the pipeline created,we can start putting our data into that from the data producer side. For that, we need to create a pipeline in scrapy which adds every scraped item to Redis and we consume it later. we add the code to the **pipelines.py** the file of scrapy project.
This would start sending the data to Redis and to verify we can check our pipeline with **redis-cli** and type LLEN 'DATA-PIPELINE-KEY’ to see the number of quotes in the data pipeline.

## Building the consumer and consuming data
As we’ve built a pipeline and a producer which can keep putting data to the pipeline independent of data consumption we are more than halfway through all we need to get data from the data pipeline and consume it according to our needs to call it a project.
we create a new directory in root , name it consumer and create a new file with the name **quotes_consumer.py** in it.
After this step, we can run scrapy spider and consumer independently which helps us in streaming data at a very high speed as data production and consumption are independent of each other.





