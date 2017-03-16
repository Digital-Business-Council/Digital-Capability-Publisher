# 9 Services Provided by the Capability Publisher 

A Digital Capability Publisher exposes two types of interfaces: 
 1. A discovery interface. This interface is a publicly available API to retrieve information stored in the Digital Capability Publisher. It gives access to a receiver’s capability information. 
 2. A management interface. This interface limits access to authorized clients and allows changes to information stored in the Digital Capability Publisher. 

A Digital Capability Publisher Provider may also decide to implement a graphical user interface to interact with business capability data. This type of interface is not defined in this implementation guide. 

## 9.1 Discovery API 
The discovery API is used during the operation of the framework. It is responsible for allowing entities in the network to discover endpoints. 
Access to discovery resources is via HTTP GET requests. 

### 9.1.1 Security 
These API’s can be made available without security over HTTP. The resource representation of a business capability record is signed with the Digital Capability Publisher private key (see 7.2 p.19). 

### 9.1.2 Service group 

#### 9.1.2.1 Purpose of the API 
The service group resource is the entry point for access points to discover a list of capabilities for a business. 

#### 9.1.2.2 Behaviour of API 
This API does not have side effects and will return a Service Group element as per the OASIS standard (OASIS, 2014). 

#### 9.1.2.3 Sequence Diagram 
Retrieving a list of capabilities can be done by corner 1, when a business user wants to determine the capability of a trading partner. Or by corner 2, where an access point finds a suitable service to send a document to. 

![getserviceAP_Logo](/images/Get-service-group-AP.PNG)

#### 9.1.2.4 Resource Location 

| | | |
| --- |------- | -----|
Request URL | http://<dcp domain>/{scheme identifier}::{id} | |
HTTP Method |SSL/TLS |Authentication Mechanism |
GET | No | N/A |

The ServiceGroup resource has the following location: 

![servicegroup-resource_Logo](/images/servicegroup-resource.PNG) 

Colons in the URL need to be encoded as per (Berners-Lee, Fielding, & Masinter, 2005).

| | | 
| --- |------- |
scheme identifier | urn:oasis:names:tc:ebcore:partyid-type:iso6523:<scheme e.g. 0151> |
id | e.g. <abn number> |

Example URL 

![servicegroupresource-URL_Logo](/images/servicegroup-resourceURL.PNG)

#### 9.1.2.5 Request Headers

| | | | |
| --- |------- | -----| -----|
**Header**| **Optional**| **Type**| **Description**|
Accept | Optional | String | text/xml |




