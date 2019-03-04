# DevSecOps - Julio Faerman

## Monolith to microservices
Stangles the monolith. Uses ALB's to direct traffic to various services.

CI/CD allows for a much faster release cycle with far fewer bugs

Infrastructure as code becomes necessary as teams start to scale

### Cloudformation
IAAS managed service. A templating language that atomically creates the infrastrucutre you require. CF itself is free, and you only pay for the use of the services it creates.

```
Resources:
  HelloBucket:
    Type: AWS::S3::Bucket
```
This would create a default S3 bucket

CF Parameters
 - string
 - number
 - List<T>
 - CSV
 - Parameter Store
 - EC2 values
  -    AZ, name etc

Resources
 - Anything on AWS. Currently over 300 on documentation
 - The CF values for AWS features often lag behind what the API actually offers

Intrinsic Fuctions
 - `Ref`
 - `Fn::GetAtt` - Gets attribute from a specific resource
 - `Fn::Sub`
 - `Fn::FindInMap`

Functions are run in the template with this syntax `CF Key: !Ref MyProperty`

Pseudo Parameters
 - AWS::AccountId
 - AWS::NotificationARNs
 - etc

These are all passed in by default to every CF deploy

Conditions
 - Fn::And
 - Fn::Equals
 - Fn::If
 - Fn::Not
 - Fn::Or

These can be used to create logic statements in the template

#### Cross stack references
Allows you to reference the outputs from 1 CF Stack and import it in another Stack using the `Fn::ImportValue: MyVar` function.

You can also use Nested Stacks. A parents stack built up of several child stacks

#### Template validation
 - cfn-lint
 - cfn-nag

CFN Nag will tell you about potential secutiry group issues etc

CFN-Lint will tell you before you push if your stack has issues with formatting

#### Drift Detection
Allows you to see what has changed between the cF Template and what is actually running in that stack now. 

#### Stack Sets
Allows you to create stacks in different regions.

## CDK Cloud Developer Kit

Can create Cloudformation YML from any DSL

## Continuous Delivery with CodeStar

Allows you to create full application pipelines with a few clicks on the Console

## Security

### Amazon Inspector
Looks for libraries with vulnerabilities, CVE's, open ports

### Cloudtrail
Automated auditing logs. Logs each API call, regardless of which client made it (cli, console, CF etc).

### AWS Config rules
Allows for automated checking of various resources to ensure that each resource is properly configured. Such as security groups on all ec2 instances

### AWS Guard Duty
A tool that is able to identify certain traffic or code behaviours and automatically trigger a lambda function to alert to. 

Things like bitcoin mining, DDoS spamming etc are all things that can be caught by it. Can be useful to help identify and detect potentially compromised instances.