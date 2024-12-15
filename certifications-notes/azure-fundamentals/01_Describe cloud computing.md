
# Introduction To Microsoft Azure Fundamentals

## What's Microsoft Azure?

Microsoft Azure is a cloud computing platform that offers various services, like:
- Hosting services
- Virtualization Services
- Account management Services
- AI and IOT services

And so on and so forth..

# Introduction to cloud computing

## What's Cloud Computing?

Cloud Computing for Azure is simply deliver computing services over the internet.
Like we said in the previous section we can have services like:

- Virtual machine services.
- Databases services.
- Network services.
- Artificial Intelligent services and Machine learning services.


## Describe the shared responsibility model

So what's the shared responsibility model?
Cloud computing services are offered from companies like Microsoft, Amazon and Google i.e Cloud Vendor..
A Normal company or a Bank will likely use these services i.e Cloud consumer
Now, there's a a clear traced line which tell what's the responsibility for each actor.
Microsoft will provide:
- Physical Security infrastracture
- Power, Cooling and network connectivity for servers.
The Bank will likely:
- Data management
- Access security

The responsibility depends on which services the Bank will use.
If The Bank will use Azure SQL the Bank it will only manage the data ingestion on the DB.
If the Bank will use a VM machine service, the bank will need to manage database patches and updates and maintaining the data and information stored in the database.

Like we said before the shared responsability model is heavily tied to the type of cloud service.
- In **SAAS** (Software as a service): There's more responsibility on the cloud vendor side.
- In **PAAS** (Platform as a service): There's more responsibility on the cloud vendor side.
- In **IAAS** (Infrastructure as a service): There's more responsibility on the 

The cloud consumer will be alway responsible for information management, device connectivity and account and identities of the people services of the organization.
The cloud provider will be always responsible for physical datacenter, physical network and physical hosts.

The subject of the responsibility various on these topics:
- Operating systems
- Network controls
- Applications
- Identity and infrastructure

![Shared Responsibility Model](../../assets/images/shared-responsibility-b3829bfe.svg)