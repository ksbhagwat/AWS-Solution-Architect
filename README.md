AWS Services
===

**aws config**

ECS /EKS - > proxy container managed service / kubernates

**Docker** - 
breaking up monoliths
service oriented architecture
batch jobs
    short lived jobs
    variety and flexibility
    elasticity
CI/CD pipelines
    packaging in docker images
    test
    depoy in prod
    
**Fargate** 
Run containers without managing servers or clusters 

**Cloud Formation**  Infrastructure service as code, define yml for all configs
Model and provision all your cloud infrastructure resources. Can create template
```
{
  "AWSTemplateFormatVersion" : "version date",

  "Description" : "JSON string",

  "Metadata" : {
  },

  "Parameters" : {
  },

  "Mappings" : {
  },

  "Conditions" : {
  },

  "Transform" : {
  },

  "Resources" : {
  },

  "Outputs" : {
  }
}
```


    
   
   

**Beanstalk**  publish a webapp without caring for infrastructure
Service Role / Instance Role

**Apache Flume**
is a distributed, reliable, and available software for efficiently collecting, aggregating, and moving large amounts of log data. It has a simple and flexible architecture based on streaming data flows.Mostly for new users who are new to aws




dynamo db - no sql database
lambda -> serverless computing platform
route 53 -> dns routing


**SQS** 
* Using SQS you can decouple components of the application so that they can run independantly
* managed queue (Simple Queue Service )
* web service that gives you aceess to message queue that can be used to store the messages while waiting for computer to process them
* standard queue (not ordered and might get duplicates )/ FIFO queue
* pull based, for push based used SNS
* 256 kb in size messages
* 1 min to 14 days retention days,default retention 4 days
* visibility time out (amt of time message is visible in SQS queue after reader picks up that message) maximum is 12 hours
* SQS gurantees that your messages will be processed at least once.
* Enable Long polling by setting the ReceiveMessageWaitTimeSeconds >0
* FIFO limited to 300 transactions per sec
* SQS short polling / Long polling . use long polling for saving money

**SNS**
* Push notifications
* all messages are stored across multiple AZ
* PUB-SUB model
* sms / sqs/ android
* multiple transport protocalss
Create Topic : access point(dynamicaly subscribe)
Subscribe
Delete Topic
Publish

HA Amazon MQ (Application migration)
Active Broker
Standard Broker

**EMR** 
Amazon Elastic MapReduce (EMR) is an Amazon Web Services (AWS) tool for big data processing and analysis

EMR -> core nodes [YARN+HDFS] 1or 2 nodes
	->task nodes [YARN] 
Autoscaling -> Task nodes can be autoscaled

EMR creation
Bootstrap actions -> while cluster is getting launched
Step -> processing commands
Presto-> fast and flexible

3V's for Big Data
Velocity
Volumne
Variety

**Redshift** 
Amazon Redshift is an Internet hosting service and data warehouse product which forms part of the larger cloud-computing platform Amazon Web Services.

unlimited concurrency/ extends data lake
Amazon's Redshift uses which block size for its columnar storage? 1MB

**Athena** 
Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL./ serverless EMR
**Glue**- > serverless for ETL/ Glue catalog in Athena
**Quicksight** -> BI tool

**Kinesis** (similar to Kafka)
platform where straming data is send 
Types:
1. Kinesis streams [shards, no storage avaialbe]
2. Firehose [firehouse + s3]
3. Analytics [data analytics on the fly]

* default data retnention is 24 hrs max 7 days
* kinesis streams consists of shards (5 transactions per sec for reads up to max of 2mbps)

File data -> S3
Streaming data -> Kinesis


copying data to s3
using nfs mounts and s3 agent data sync
using s3distcp to copy from s3 to hdfs

connectivity between on premises and AWS
1. VPN
2. AWS direct connectivity
3. amazon S3 multipart data load
4. AWS snowball [physical data transfer ]


replicate data in multiple regions so that if one region is down you can still get the data
batch processing vs stream processing

decouple collection and processing 
preserve the client ordering 
collect multiple strams together
consume in parallel


amazon firehose -> data loader app for kinesis so that you dont have to configure and program for kinesis
instread of using KCL use Spark streaming and EMR

firehose atleast 60s of latency while kinesis sub 1s latency
kinesis analytics


Streams -> Kinesis
Table Streams -> Dynamo DB


<b>Amazon Neptune</b> is a fast, reliable, fully managed graph database service that makes it easy to build and run applications that work with highly connected datasets. ... Amazon Neptune is highly available, with read replicas, point-in-time recovery, continuous backup to Amazon S3, and replication across Availability Zones. Neo4j alternative

**EFS** - shared file storage. Network file storage for EC2 instances.

**HBase/Cassandra** -> columnar data store
shard 


DAX -> 
**redshift** - datawarehouse

Intelligent tiering service moves the data between diffrent s3 services


Amazon Elasticsearch Service is a popular open-source search and analytics engine for big data use cases such as log and click stream analysis. 

**GraphX** is Apache Spark's API for graphs and graph-parallel computation.
smaller object -> dynamo db
bigger objets -> s3 because dynamodb has more storage cost

S3 as data lake


Athena Time taken to execute the query
(Run time: 18.12 seconds, Data scanned: 90.74 GB)
(Run time: 19.44 seconds, Data scanned: 13.08 GB)
  Partition compressed data
  (Run time: 6.02 seconds, Data scanned: 0 KB)	-> to create partition data
  (Run time: 19.69 seconds, Data scanned: 432.46 MB)
  Parque
  (Run time: 3.03 seconds, Data scanned: 1.97 MB)
  

Master node on dedicated EMR while Task nodes can be on Spot price

Auto scaling Rules based onYARN if memory is less than 15% for 5 min period 

hive -d SAMPLE=s3://aws-tc-largeobjects/AWS-200-BIG/v3.1/lab-4-hive/data -d DAY=2009-04-13 -d HOUR=08 -d NEXT_DAY=2009-04-13 -d NEXT_HOUR=09 -d OUTPUT=s3://hive-bucket-123/output/


File sizes -> spliltabble > parquet + snappy 2G-4G >csv,json
				non splittable 


use kinesis firehose to combine the files if it is smaller (1MB-128MB)

Hive (reliability + more features) <  Spark SQL < Presto (less reliable ) < Redshift (Highest performance) defining schema

**Dynamodb**
* 	Data is stored on SSD
* 	Spread acroos 3 geographically distinct data centers
* 	eventual consistent reads
* 	stongly consistent reads
	
	


Apache Zappelin : Jupyter notebook with spark integration
JupyterHub -> jupyter notebook applications/ sagemaker

Hue -> webui for hadoop browser based / facilitates collaberatin
Ganglia (individual workers) vs cloud watch (overall metrics)/ Hadoop UI monitoring



**Amazon Redshift** is an Internet hosting service and data warehouse product which forms part of the larger cloud-computing platform Amazon Web Services.
	Data Warehousing Tool
	Business Intelligence Toool
	only one Availability zone
	

**AWS Glue** is a fully managed ETL (extract, transform, and load) service that makes it simple and cost-effective to categorize your data, clean it, enrich it, and move it reliably between various data stores

**X- ray** debug lambda functions


**cloud front**
content distribution static contents cache (CDN)
Edge location is seperate from AZ. its the location where content is cached
origin : origin of all the files that CDN will distribte this can be S3 bucket / ec2 instance /ealstic load balancer /route 53
edgelocations are not read only . Time to Live (TTL)

**AWS storage gateway** 
transfer data between in house data center to AWS
1. 	File Gateway
1. 	Volume Gateway
1. 	Cached volume


**Rekognition**
Deep learning based visual analysis service

**Step Functions**
state machine - workflow template
task - lambda fnction
activity - handle for external compute

Resources
* https://acloud.guru/forums/aws-certified-solutions-architect-associate/discussion/-LZipqkEptfvidSZs_5i/passed_aws_ssa%20%20Follow%20Responses
* https://d1.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf
* https://www.aws.training/learningobject/curriculum?id=20685
* https://gist.github.com/leonardofed/bbf6459ad154ad5215d354f3825435dc
* https://blog.newrelic.com/engineering/aws-certified-solutions-architect-associate-exam-prep/
* AWS Console recorder chrome plugin. Generates scripts when done in ui

### AWS Guard Duty
Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts, workloads, and data stored in Amazon S3.Cloud watch is used along with lambda to watch the events.


### AWS Inspector

arn format#
arn:partition:service:region:account_id:resource
* partition : aws|aws-cn
* service : s3| ec2| rds
* region : us-east-1 | eu-central_1
* account_id
 
**AWS Control tower** 
Service Control Policy called as guard rails controls all users at one place like block all SSH connections

**Systems Manager**
> you can use to view and control your infrastructure on AWS
> you can view operational data from multiple AWS services and automate operational tasks across your AWS resources

**Elastic Transcoder**
1. Media transcoder in cloud
2. convert media files from original source format to different format that will play on smartphones , tablets ,pcs etc
3. provides transcoding presets for popular formats
Pipeline-> preset ->Job

### AWS Cognito
* User pools 