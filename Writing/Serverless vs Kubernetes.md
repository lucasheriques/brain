# Serverless
Serverless is not the absence of server. You're abstracting them - they're managed by the cloud provider. It has four principles:

1. Servers are abstracted
2. Pay for what you use
3. Have high availability out of the box
4. Be able to scale on demand

## Serverless stack

The function-as-a-service takes care of abstracting the server. You feed it a zip file or the container image, and the cloud provider will instantiate the container and execute the function.

The other parts in the serverless stack handles storage, eventing, orchestration, ETL, analytics, etc.

![[CleanShot 2023-03-10 at 01.50.04@2x.png]]

# Serverless Explained
It's a misnomer used to describe servers in the cloud that require zero configuration or maintenance from the developer.

It's kinda how we pay for water in cities - we pay for the amount that we use. But, instead of water, we pay for the amount of CPU and memory that we use.

Examples are AWS Lambda, Google Cloud Functions and Azure Functions. They allow you to run your backend code across their global datacenters.

The beauty of this approach is that you only need to concern yourself with writing the code and uploading. No need to worry about operation system, configure networking, provision capacity. The cloud handles that for us behind the scenes.

From an architectural standpoint, it allow us to develop and test each business requirement independent of a bigger monolitch system.