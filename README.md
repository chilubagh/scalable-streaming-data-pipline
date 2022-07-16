

## Introduction

Data streaming is part of a data engineers job.In this project, I am going to build a very simple and highly scalable data streaming pipeline using Python. Data streaming is the process of transmitting a continuous flow of data.

![Data pipline](https://user-images.githubusercontent.com/51442225/179332300-80b9eb84-30c7-475d-96eb-459b7a13ee5b.png)

One side of the pipeline would have some or at least one data producer who would be continuously producing data and on the other side, we would have some or at least one data consumer who would be consuming that data continuously.

## Architecture

![Pipeline architecture](https://miro.medium.com/max/1400/1*9m4bX85qMH3jAeimuDR_kQ.png)

I will be using Redis as data pipeline and using a very simple data scraping microservice using Scrapy independently as a data producer and a separate microservice as a data consumer.

## Building the data Producer

I am building a simple python project with scrapy in a virtual environment.
I run the command given below to create an empty Scrapy project.

`scrapy startproject producer`

> > > > > > > 586004c78c201eb23e9570bc43f0f084ad355ce8
