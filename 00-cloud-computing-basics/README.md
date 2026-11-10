# 00 - Cloud Computing Basics

## What I Learned

Cloud computing means using IT resources, such as servers, storage, databases, and applications, over the internet instead of owning and running them myself. I pay for what I use, and I can start or stop it when I need to.

## The Two Key Ideas

- **On-demand:** I can get resources as soon as I need them, without buying hardware or waiting weeks for it.
- **Pay-as-you-go:** I pay only for what I use, instead of paying a large amount upfront.

## Why Companies Use It

Running my own data center would mean paying for space, power, cooling, maintenance, and staff, and I would have to guess how much capacity I need. With the cloud, the provider handles the hardware, and I can scale up or down as my usage changes.

## Types of Cloud

- **Public cloud:** a provider such as AWS shares its infrastructure over the internet.
- **Private cloud:** one organization runs its own cloud with dedicated resources.
- **Hybrid cloud:** a mix of on-premises systems and public cloud.

## Service Models

- **IaaS (Infrastructure as a Service):** I get raw building blocks, such as servers and storage, and manage the operating system and everything above it. Example: Amazon EC2.
- **PaaS (Platform as a Service):** I manage only my application and data, and the provider manages the platform. Example: AWS Elastic Beanstalk.
- **SaaS (Software as a Service):** I just use a finished product. Example: Gmail.

## AWS Basics

- **Region:** a geographic area, such as `us-east-1`, that contains several data centers.
- **Availability Zone (AZ):** one or more isolated data centers inside a Region. Using several AZs keeps an application running if one fails.
- **Edge location:** a site close to users that delivers content quickly.

## Shared Responsibility

Security in the cloud is shared:

- **AWS** secures the cloud itself, including the facilities, hardware, and core software.
- **I** secure what I put in the cloud, including my data, access settings, and firewall rules.

## Key Takeaway

Cloud computing is a way of using IT: on demand, metered, and shared. AWS provides it, but I stay responsible for the security of my own resources.

## Sources

- AWS, "What is Cloud Computing?": https://aws.amazon.com/what-is-cloud-computing/
