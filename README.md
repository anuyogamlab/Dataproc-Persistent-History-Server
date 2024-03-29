# Dataproc-Persistent-History-Server

The challenge with ephemeral clusters and Dataproc Serverless for Spark is that you will lose the application logs when the cluster machines are deleted after the job. 

Persistent History Server (PHS) enables access to the completed Hadoop and Spark application details for the jobs executed on different ephemeral clusters or serverless Spark. It can list running and completed applications. 

PHS keeps the history (event logs) of all completed applications and its runtime information in the GCS bucket, and it allows you to review metrics and monitor the application at a later time. 

PHS is nothing but a standalone cluster. It reads the Spark events from GCS, then parses and presents application details, scheduler stages, and task level details, as well as environment and executor information, in the Spark UI. These metrics are helpful for improving the performance of the application. Both the application event logs and the YARN container logs of the ephemeral clusters are collected in the GCS bucket. 

These log files are important for engaging Google Cloud Technical Support to troubleshoot and explore. If PHS is not set up, you have to re-run the workload, which adds to support cycle time. If you have set up PHS, you can provide the logs directly to Technical Support.

The following code block inside setup/ creates a Persistent History server. 

# Best Practices of PHS
https://cloud.google.com/blog/products/data-analytics/running-persistent-history-servers
