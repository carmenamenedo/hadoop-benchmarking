# 🐘 Hadoop Benchmarking

Big Data benchmarking project focused on **Hadoop, HDFS and MapReduce**, developed on a shared distributed cluster.

The project explores Hadoop configuration, distributed data processing and performance through several benchmarks, including **WordCount, TeraGen, TeraSort, TeraValidate and TestDFSIO**.

Developed as part of my MSc in Big Data & Artificial Intelligence.

## 📌 Project Overview

The main objective of this project was to work with a real Hadoop cluster and analyze how its configuration and level of parallelism affect distributed processing performance.

The cluster was accessed through SSH and monitored using **HUE** and **Cloudera Manager**.

The project includes:

- HDFS configuration analysis
- MapReduce job monitoring
- WordCount execution
- Large-scale data generation with TeraGen
- Distributed sorting with TeraSort
- Result validation with TeraValidate
- HDFS write performance benchmarking with TestDFSIO
- Analysis of the impact of the number of reducers

## 🛠️ Technologies & Tools

- Apache Hadoop
- HDFS
- MapReduce
- YARN
- HUE
- Cloudera Manager
- Linux
- Bash
- SSH

## ⚙️ Hadoop Cluster Configuration

The observed cluster configuration included:

| Parameter | Value |
|---|---:|
| HDFS block size | 128 MiB |
| HDFS replication factor | 3 |
| Default MapReduce reducers | 4 |
| Hive bytes per reducer | 64 MiB |
| Maximum Hive reducers | 1099 |

## 📝 WordCount

A WordCount job was executed using a large text file stored in HDFS.

The execution was monitored through HUE to analyze:

- Number of Map tasks
- Number of Reduce tasks
- Execution time
- Job status
- HDFS data processed

One of the executions completed successfully with:

- **5 Map tasks**
- **4 Reduce tasks**
- **~55 seconds**
- Status: `SUCCEEDED`

The experiment also showed how the number of Map tasks can vary depending on how Hadoop divides the input into splits.

## 🏗️ TeraGen

TeraGen was used to generate a large dataset for the sorting benchmark.

### Results

- **40,000,000 records**
- **100 bytes per record**
- **~4 GB generated**
- **2 Map tasks**
- **0 Reduce tasks**
- Status: `SUCCEEDED`

## ⚡ TeraSort Benchmark

TeraSort was used to study distributed sorting performance.

The ~4 GB dataset generated with TeraGen was sorted using different numbers of reducers.

### Performance Results

| Reducers | Execution Time |
|---:|---:|
| 1 | 67.00 s |
| 2 | 60.00 s |
| 3 | 52.40 s |
| 4 | 50.22 s |
| 5 | 44.60 s |
| 6 | 40.90 s |
| 7 | 40.51 s |
| 8 | **37.97 s** |

### 📈 Result

Increasing the number of reducers from **1 to 8 reduced execution
