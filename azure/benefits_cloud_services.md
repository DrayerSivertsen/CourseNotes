# The benefits of using Cloud Services
This modules goes into the key benefits that come with getting your computing resources from a cloud provider

## Benefits of High Availavility and Scalability
The biggest considerations of deploying cloud applications are, uptime (availbility) and the ability to handle demand (scale)

### High Availability
Focuses on having resources being available a maximum amount of time

Azure is a highly available cloud environment with uptime guarantees depending on the service (part of the service level agreement).

### Scalability
Scalability refers to the ability to adjust resources to meed demand. If you suddenly experience peak traffic and your system is overwhelmed , the ability to scale means you can add more resources to better handle the increased demand

**you arent overpaying for services. Because cloud comsumption-based model, you only pay for what you use.

Two types of scaling"
- vertical scaling
    - if you were deploying an app and you needed more processing power, you could vertically scale up to add more CPU or RAM to the VM
    - conversly you could scale down to less supported CPU power
    - changing version to accomadate for more or less compute power
- horizontal scaling
    - jump in service demand, add additional virtual machines or containers, scaling out
    - more VM's to handle more traffic
    - also works in the reverse

## Benefits of Reliablity and Predictability
Reliablity and predictability are two crucial cloud benefits that help you develop solutions with confidence

### Reliability
The ability of a system to recover from failures and continue to function. Also a pillar of the Microsoft Azure Well-Architected Framework

### Predictability 
Lets you move forward with confidence. Predictability can be focused on performance predictablity or cost predictability. 

Performance predictability focuses on predicting the resources needed to deliver a positive experience for your customers. Autoscaling, load balancing, and high availability are just some of the cloud concepts that support it. 

Cost predictability focuses on predicting or forecasting the cost of cloud spending. You can track your resources in real time, monitor resources to ensure that you are using them in the most efficient way, and apply data analytics to find patterns to better plan deployment. 

## Benefits of security and Governance
Cloud based auditing helps flag any resources that's out of compliance with your corporate standards and provides mitigation strategies. Depending on your operating model software patches and updates may automatically be applied. 

You can find a cloud solution that matches your security needs. Azure offers services for all levels of security and control needs and due to its over-the-internet nature it is suited to handle things like DDoS attacks, making your network secure. 

## Benefits of Manageability
Management of the cloud
- automaticallly scale resource deployment based on need
- deploy resources based on preconfigured template, removing the need for manual configuration
- monitor the health of resources and automatically replace failing resources
- receive automatic alerts based on configured metrics in real time

Management in the cloud
- through web portal
- using a command line interface
- using APIs
- using PowerShell