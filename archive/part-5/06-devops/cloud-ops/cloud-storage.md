# Cloud Storage

### Retail Cloud Storage \(File storage\)

* Google Drive
* Dropbox
* SkyDrive
* Box
* iCloud

### Enterprise Data Storage

* Google Cloud
* Amazon Web Services
  * S3 \(Simple Storage Service\) - Durable object storage for all types of data
  * Glacier - Archival storage for infrequently accessed data
  * EBS \(Elastic Block Store\) - Block storage for use with Amazon EC2
  * EFS \(Elastic File Store\) - File storage for use with Amazon EC2
* Microsoft Azure

### Storage Types

##### Block Storage

Typically used when data is stored in volumes, referred to as blocks. Each block acts as an individual hard drive and is configured by storage administrator. These blocks are controlled by a server based operating system, that are generally assessed by a fiber channel or ethernet or other types of network. Because the volumes are treated as individual hard drives, block storage works well for storing variety of applications such as file system and databases. While block storage devices tends to be more complex and expensive in file storage, they also tend to be more flexible and higher performing.

Amazon's EBS provides a virtualized storage area network with logical volume management provisioning via a simplified web services interface. Using a block storage offering, a logical disk drive of a given size and throughput can be connected to any cloud instance.

##### Object Storage

Object storage, such as AWS S3 and Microsoft Azure Blob storage, is optimized for storing large volumes of unstructured data. Both objects and files are associated with metadata about what they contain. Each object is assigned a unique identifier. Data is stored as immutable objects, the contents of which can only be written or updated in their entirety.

Supports linear scalability, large sizes. They're web friendly, firewall friendly, HTTP friendly, REST accessible. Objects can be extensible to multiple policies, and able to retain data as long as the object lives. No locking and Geo Scale.

##### File Storage

Stores data in the hierarchical set of folders. Inexpensive to maintain. Data can be accessed using file systems such as NFS, Unix and Linux, or SMB protocol. File systems can be of type NFS \(Network File System\), SMB \(Server Message Block\), or others that reside in clouds or on premises. The most traditional service type is a shared file system, which offers multiple clients the ability to access a single shared folder. Example Amazon EFS.

### Example: Big Data

* Leverages Storage
* Expandable as need arises
* High performing

In this example we have S3 + EMR \(Elastic Map Reduce\). AWS is form of Hadoop. Application server, located in corporate data center, communicates with AWS Direct Connect \(provides a gateway to AWS\), which in-turn communicates with AWS S3, and then S3 communicates with multiple EMR clusters.

### Example: Backup and Recovery

In this example, Media server with cloud connector communicates with AWS Direct Connect via HTTPS/API, which in-turn communicates with S3, S3-IA and Amazon Glacier.

