# Cloud backend for realtime applications - Martin Beeby

Hard real time - actual real time instant transactions
Soft real time - mostly real time which most people need

## What is Real Time?
Seeing changes in one place appear in the other. Messaging systems, hotel bookings, multi player games.

### Evolution
Long Polling => Forever Frames => Server Sent Events => Web Sockets

## SignalR on AWS
Supports websockets, server side events and long polling and gracefully degrades depending on client support

`services.AddSignalR()` is all that is needed to install it in .NET Core apps in the `Startup.cs`.

.NET SignalR apps can be easily deployed to Elastic Beanstalk, and use an Elasticache backplane for it's messaging for pubsub

## API Gateway and Websockets
API Gateway creates the web socket connection, and behind the scenes can pass requests on to Lambda etc. API Gateway manages all the connections.

When the Lambda returns its request the connection ID passed to it can be stored in Dynamo to store state and makes a `POST` request back to a special endpoint that is able to communicate back to each connected client

## AppSync
The managed GraphQL service from AWS. It supports real time connections out the box, as a fully managed service