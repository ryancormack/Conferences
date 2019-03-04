# Building Global Services with Serverless - Julio Faerman and Adrian Hornsby

## Global architecture
Latency to end users and local laws and governence mean it is necessary to distribute your application around the world

Each AWS Region has 2-6 Availability Zones. Each AZ gives an extra layer of redundancy. An AWS load balancer can be used to route traffic between AZ's. Route 53 can be used to route traffic between entire regions.

Building an Active Active application will give your end user the best experience and have region level redundancy, down to feature level issues

### Serverless
No provisioning and no management of the services. Pay for what you use. Automatic scaling

## Building global features
CAP Theorem

Consistency
 - Data is consistent. All nodes are the same state

Availability
 - Data is consistent. All nodes are the same state

Partition Tolerance
 - Every request is non-failing
 - Serivce still responses as expected if some nodes crash or isolate

In the presence of network partition, you must choose between consistency and availability. Latency/availability can often have real world effects in cost.

Eventually consistent data becomes necessary

Global replication is done asynchronously.

### DynamoDB Global Tables
Fully managed, master, master, database with single digit millisecond read times.

Eventually consisten data replication between regions, with writes always occurring at the endpoint closest to the client

Global tables have additional AWS metadata properties on them, such as the last updated region and the created region. 

Global Tables just use Dynamo Streams under the hood, so streams need to be enabled on each of the tables in the Global Tables setup to ensure data can be replicated

Dynamo DB last write always wins when data is written to the same partition key in various regions

### Global routing
Route53 is the default way of global routing in AWS.

Latency routing will send the use to the lowest latency routing. AWS maintains a list of latencys from client to endpoint globally so Route53 knows where to route the request.

Geographical routing will send the user to a pre determined geographical location, regardless of latency

Weighted round Robin routing can send `x` amount of traffic to one endpoint and another amount to another endpoint

Failover routing will always send traffic to the primary node, unless thre is a failover scenario when all traffic would go to the failover region

## AWS Global Accelerator
Improves global application availability and performace. Dramatically reduces the number of hops the client has to make before reaching any part of the AWS infrastrucutre. Using Anycast, the traffic can go straight from the ISP's network direct to the AWS network

![global dynamo setup](global_dynamo.jpg)