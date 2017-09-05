# Cloud Operating Model

There are many reasons that a Cloud Strategy may be adopted in business. Existing IT estates may be showing their age, new challenges may be emergent due to changing customer behaviour or competitors may be moving forwards gaining a competitive advantage that you seek to match. Whatever the root impetus, the Cloud Strategy requires a comprehensive Operating Model to deliver most effectively against the Cloud Strategy. 

This document, produced by Elastacloud Limited, attempts to lead a discussion in building a comprehensive operating model.  

## Definitions

- In-house technology 
    - Our IT Team and everything they influence in our technology stack
- Vendor supplied technology
    - Those cloud services we can buy in 

## Cloud Fundamentals

The core of the operating model is to expand the productivity and capability of the in-house technology team by leveraging the available vendor supplied technology. The range of the vendor supplied technologies varies from supplier to supplier, but is generally regarded as broad at this stage in Cloud evolution.

Vendor supplied technologies should be measured along the following lines:

- *PaaS First* - Prefer services that abstract significant overhead from the in-house technology team
  - *Buy vs build* - Evaluation of the effort required to simulate the functionality versus the cost of any platform service gives a ROI for adoption
  - *Lockin metric* - Evaluation of the effort required to simulate the functionality versus the availability of equivalent platform services gives a portability metric  
- *OSS* - Prefer services that offer their internals as Open Source software licenses

Core Fundamentals

1. Agility
1. Scale
1. Economy

## Characteristics of an Agile Cloud solution

1. Cloud solutions are controlled through communication with a Fabric, that giant builder of systems that resides inside the datacentre. 
1.	Communication with the Fabric is through secured API interaction
1.	The Fabric communication is software mediated through portals and that could be software that you control
    1.	You may define this software as scripts or compiled applications
    1.	In pure terms, the software generates the API traffic that is equivalent to that you may generate in a portal
1.	On receipt of a request, the Fabric will immediately provision software, allowing for real time infrastructure provision

It is no longer a fact that we are limited by our ability to provision resources in a timely manner. This allows us to be free from concerns of environment availability. Furthermore, capacity contention disappears in a cloud context, allowing plurality of effort and concurrency of environment.  We can build identical estates for dev/test scenarios. We can stand up UAT environments for limited duration and be confident that they are equivalent to production. We can react to unexpected business events and provide additional resource to meet the requirements.

The agility builds to a key benefit of the cloud; focus. Where optimally applied, a business can focus on their business need without having to support this with an extensive IT operation. 

There are many places where a Cloud platform can provide additional services on top of raw capacity; for instance in web, database or storage hosting. These services don’t require you to run Virtual Machines are typically called Platform as a Service offerings; and they are regarded by Elastacloud as the pinnacle of cloud deployments. This is not to say that Infrastructure as a Service (such as Virtual Machines) is fundamentally wrong; instead that it is wrong to incorrectly use IaaS where PaaS would suffice. 

In some solutions, IaaS is the only option. Where this is the case, exposing PaaS like services to business users by using IaaS is the best service an IT team can provide. 

## Characteristics of a Scalable Cloud solution

1.	From the point of view of the Fabric consumer, the Cloud is of infinite scale; it has infinite capacity in storage and compute
1.	Provisioning resources within the Cloud allows for geographic distribution of workload with no privilege; North Europe and East Japan are equivalent technologically
    1.	It should be noted that economically there may be variance due to vendor issues such as land price differences between Dublin and Tokyo
1.	Once provisioned Cloud Services are mutable in their scale; 
    1.	they may grow or shrink as differing demands are placed on them
    1.	Such abilities include the notion of auto-scale and elasticity

There are two primary mechanisms for scale within a cloud scenario. These are termed scale up – the provision of additional resource capacity within a single node (more CPU, more RAM, more disk) and scale out – the provision of additional nodes with identical capacity into an existing set of nodes (more machines). Scale Up has a finite limit and whilst the limit may be high, it is a hard limit – there are not always bigger machines. Scale Out offers the consumer the notion of infinite scale – there are always more nodes to add in. 

There are examples where scale out is problematic, particularly with legacy codebases or vendor systems not designed or licensed to scale in this way. Furthermore, some systems (such as large scale analytics systems) require a relatively high starting point on the scale-up proposition and scale out might then prove economically challenging. 

### Infrastructure

### Platform

### Software

### Cloud Native 

(Interoperability between Platform/Software Services)

## Cloud Economy and Cost Management

Time/Throughput equality. 

There are some key thought processes that Elastacloud has adopted when building this solution. The document, the project and the solution needs to be viewed through these glasses, with this mind-set, from this position of understanding. These are outlined here in order that the overall approach is understood by the reader. 

1.	Economy
    1.	Cloud solutions are pay-as-you-go, a pay per consumption model
    1.	Turning off utilised resources immediately reduces the associated expense
    1.	Linearly scalable resources can be reduced to 1 unit of distribution in time; 
        1.	(input domain size / distribution)  * duration * cost per duration
        1.	reading 60 files each taking 1 minute on a 1 core machine costs 60/1 * 1 * 1 = 60 core minutes
        1.	reading 60 files each taking 1 minute on 60 1 core machines costs 60/60 * 60 * 1 = 60 core minutes

For some workloads we can execute work without regard for time. As we scale, we pay monotonically increasing amounts for our compute. If we can decrease the total duration of our execution by a corresponding amount then we can effectively execute in 1 time unit, defined by the minimum load at which we can slice and distribute our work. 

When we look at this 1 time unit, we stack resources up to achieve execution within that 1 time. Thus time ceases to be a dimension in which we have to plot economy.  60 machines can do in 1 minute what 1 machine can do in 1 hour. 360 machines can do in 1 second what 1 machine can do in 1 hour. 1800 machines can do in 200 milliseconds what 1 machine can do in an hour. 200 milliseconds is generally regarded to be the point at which humans stop noticing complex changes and instead experience the change as instantaneous. So something that would take a machine an hour to execute can be done instantly on 1800 machines. 

Whilst exaggerated; this is exactly how the Cloud should be used. In current clouds, this is not always possible as the granularity of billing is often 1 minute, but in future clouds this may not be the case. 

Even with 1 minute granularity; 60 machines for 1 minute costs exactly the same as 1 machine for 60 minutes. Therefore, for work that can be distributed, it is Elastacloud’s view that we must always distribute to the maximum level, as the benefit is with the customer. 


### On-demand resources

### Scaling

### Billing

#### Partitioning of Resources

#### Tagging and Policy

## Security

Key questions:

* Security starts at the client: controls that have to be in place in relation to the security hardening of devices
* Cloud side 
    * Data
    * Runtimes
    * Secrets

### Separation

### Identity

### Securing resources

### Monitoring

## Availability

### Geo-redundancy

### Reproducable deployments

### Transient environments

### Disaster Recovery

### Business Continuity

## Skills

### Adoption 

### Continuous Training

### Advocates

# Reusability
All Cloud artefacts should be stateless as infrastructure with a path to restoring state from centralised repositories where rehydration is required. As such the cloud artefacts become freely exchangeable, with the individual infrastructure identity as inconsequential as waves in the sea. 

## Deployable to any division

All operational deployment scripts should be parameterised and accounted in a common and consistent manner. The use of Tags combined with policy preventing deployment without Tags enforces a model of operation that is governed and entitled. 

> This Cloud Operating Model takes IT from a cost centre to a profit centre of our business. 

## Common Identity model and roles
share insights
efficiences of scale (people, costss)
Common tools and technologies