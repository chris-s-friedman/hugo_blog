---
title: "Using dlt to load data about airplanes into a database"
date: 2025-08-01T00:01:00-05:00
draft: true
type: "post"
slug: "dlt_airframes"
tags:
  - dlt
  - postgres
  - data engineering
---

I've been experimenting with trying out new data engineering tools to ETL data into a warehouse. In my office, we're a python shop that most often uses [Meltano](https://meltano.com/) for getting data into our postgres warehouse.  In my spare time, I've been trying to experiment with different tools, so in this post, I'm going to talk about how I used a different ETL tool, [Data Load Tool (dlt)](https://dlthub.com/) to extract and load data into a PostgreSQL database in my homelab.

## About dlt

## A note about the data being loaded

## dlt project structure

A dlt project has two key sets of files: configuration files and pipeline python scripts. The configuration files use TOML to define key data about an ETL pipeline. Data in those configuration files are used to setup the pipeline and used when the pipeline is run.

### Configuration Files

#### `pyproject.toml`

#### `.dlt/config.toml`

#### `.dlt/secrets.toml`

### ETL pipeline script

## Running the pipeline