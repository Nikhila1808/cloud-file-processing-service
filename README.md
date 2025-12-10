Cloud File Processing Pipeline

This project implements a cloud-native file ingestion pipeline using Java 21 and Spring Boot.
It provides APIs for file uploads, stores files in S3 (via LocalStack), triggers a processing function that reads the file, extracts metadata, and publishes a completion event to a queue.

The architecture simulates AWS S3, Lambda, and SQS using LocalStack for local development.

Architecture

             Client
               |
               | POST /api/files/upload
               v
+--------------------------------------+
|            File Controller           |
+--------------------+-----------------+
                     |
                     v
+--------------------------------------+
|             File Service             |
+--------------------+-----------------+
                     |
                     v
+--------------------------------------+
|               S3 Bucket              |
|     (LocalStack - File Storage)      |
+--------------------+-----------------+
                     |
               Event Trigger
                     |
                     v
+--------------------------------------+
|         File Processing Function     |
|     (Simulated AWS Lambda Logic)     |
+--------------------+-----------------+
                     |
                     v
+--------------------------------------+
|                 SQS Queue            |
|      (LocalStack - Processed Event)  |
+--------------------------------------+

Key Features

File upload REST API

S3-based file storage

Lambda-style automatic file processing

Event publishing to SQS

LocalStack support

Clean microservices structure

Easily extendable to real AWS

Run with Docker
docker-compose up --build
