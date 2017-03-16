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


#### 9.1.2.6 Status Codes & Error Conditions 

| | | | |
| --- |------- | -----| -----|
**HTTP Status Code**| **Message**| **Category**| **Additional Info**|
200 | Ok | Success | Returns a ServiceGroup element | 
404 | Not Found | Error | The origin server did not find a current representation for the target resource or is not willing to disclose that one exists. |
5xx | Server Error | Error | Any appropriate HTTP server error |

#### 9.1.2.7 Example Responses 

HTTP RESPONSE CODE: 200 (Ok) 

#### 9.1.2.8 Response Headers 

| | | | |
| --- |------- | -----| -----|
**Header**| **Optional**| **Type**| **Description**|
Content-Type | Mandatory | String | text/xml |

#### 9.1.2.9 Response Body – text/xml 

An example of a service group resource representation: 

![Servicegroup-representation_Logo](/images/Servicegroup-representation.PNG)


#### 9.1.2.10 Response Field Reference 

See section 7.1.2 Service Group. 

### 9.1.3 Signed Service Metadata

### 9.1.3.1 Purpose of API 
Allow retrieval of a business capability for a particular document type. This can be done via an intermediary step which involves retrieving a list of document locations for a document identifier. Alternatively, the client can retrieve a signed service metadata document by accessing the resource with the participant identifier and document identifier. 

#### 9.1.3.2 Behaviour of API

This API does not have side effects and will return a Signed Service Metadata element as per the OASIS standard (OASIS, 2014).

#### 9.1.3.3 Sequence Diagram

![getserviceAP_Logo](/images/Get-service-group-AP.PNG)

#### 9.1.3.4 Resource Location

| | | |
| --| ----| ----|
Request URL | http://<dcp domain>/{scheme identifier}::{id}/services/{document identifier type}::{root namespace}::{document element local name}[##{Subtype identifier}] | |
HTTP Method | SSL/TLS |Authentication Mechanism | 
GET | No | N/A |

A signed service metadata resource has the following location: 

![Signedservicemetadataresource_Logo](/images/Signedservicemetadata-resource.PNG) 

Colons in the URL need to be encoded as per (Berners-Lee, Fielding, & Masinter, 2005). 

| | |
| ---| ----|
scheme identifier | urn:oasis:names:tc:ebcore:partyid-type:iso6523:<scheme> |
Id |E.g. <ABN Number> Other identifier types defined by iso6523 are supported. |
Document identifier type | dbc-docid |
Root namespace | urn:www.digitalbusinesscouncil.com.au:dbc:einvoicing:doctype:core-invoice:xsd |
Document element local name | core-invoice-1 |
Subtype identifier | urn:www.digitalbusinesscouncil.com.au:dbc:einvoicing:process:einvoicing01:ver1.0 |


Example

![Signedservicemetadata-resourceexample_Logo](/images/Signedservicemetadata-resourceexample.PNG)


#### 9.1.3.5 Request Headers

| | | | |
| ---| -----| ---| ---|
**Header**| **Optional**| **Type**| **Description**| 
Accept | Optional | String | text/xml which is the default |

#### 9.1.3.6 Status Codes & Error Conditions

| | | | |
| ---| -----| ---| ---|
**HTTP Status Code** | **Message** | **Category**| **Additional Info**|
200 | Ok | Success | |
404 | Not Found | Error | The origin server did not find a current representation for the target resource or is not willing to disclose that one exists. |
406 | Not Acceptable | Error | The resource identified by the request is only capable of generating response entities which have content characteristics not acceptable according to the accept headers sent in the request. |
5xx | Server Error | Error | Any appropriate HTTP server error |


#### 9.1.3.7 Example Responses

HTTP RESPONSE CODE: 200 (OK)

#### 9.1.3.8 Response Headers

| | | | |
| ---| -----| ---| ---
|**Header**| **Optional**| **Type**| **Description**| 
Content-Type | Mandatory | String | text/xml |


#### 9.1.3.9 Response Body -text/xml

An example response. The actual signature block has been omitted.

![response-body_Logo](/images/response-body.PNG)

#### 9.1.3.10 Response Field Reference

See section 7.1.1 Signed Service Metadata.

## 9.2 Management API

A management API may be implemented by a Digital Capability Publisher Provider. Management of information in a Digital Capability Publisher may also be offered through a web based user interface. This section describes an example of a management API using the HTTP protocol. 

### 9.2.1 Security

The management APIs must only be made available over HTTPS using TLS1.2 as a minimum. Fallback to earlier versions of TLS or SSL must not be used. TLS versions with known vulnerabilities must not be used. 

The management APIs are protected and requires clients to authenticate using a client certificate. The client as well as server certificates for both access points and Digital Capability Publishers are published in the Digital Capability Locator and should be used to verify peer certificates. 

### 9.2.2 Create and Update Service Group
#### 9.2.2.1 Purpose of the API

Create or update an entry for a participant in the Digital Capability Publisher. This method can be used to add extensions to a participant entry in the Digital Capability Publisher. When updating the Service Group, the request must include a Service Group element. This will not update existing Service Metadata and Service Metadata Reference elements should not be provided.

#### 9.2.2.2 Behaviour of API

This method is idempotent and the resource will only be created once. If the resource exists and the body is empty, nothing changes and the method returns 200 Ok. If a ServiceGroup element is provided it will replace the existing one. 

If the resource does not exist, a resource is created for the provided location.

#### 9.2.2.3 Sequence Diagrams

![create-service-group.Logo](/images/Create-service-group.PNG)

![update-service-group.Logo](/images/Update-service-group.PNG)

#### 9.2.2.4 Resource Location

| | | |
| ---| ----| ---|
Request URL | http://<dcp domain>/{scheme identifier}::{id} | |
HTTP Method | SSL/TLS | Authentication Mechanism |
PUT | Yes | Client Certificate |

The Service Group resource has the following location:

![servicegroup-resource_Logo](/images/servicegroup-resource.PNG)

Colons in the URL need to be encoded as per (Berners-Lee, Fielding, & Masinter, 2005).

| | |
| ---| ---|
scheme identifier | urn:oasis:tc:ebcore:partyid-type:catalog-identifier:scheme-in-catalog |
id | <identifier>  E.g. <ABN Number> |





Example URL
![servicegroup-resourceURL_Logo](/images/servicegroup-resourceURL.PNG)

#### 9.2.2.5 Request Headers

#### 9.2.2.6 Request Body

The request body may optionally contain a ServiceGroup element. The ServiceMetadataReferenceCollection element is not required and should be ignored. This element is implied by the document resources assigned to a participant. 

This method does allow updates to extension elements.

#### 9.2.2.7 Request Field References

See section 7.1.2 Service Group. The request should not provide a ServiceMetadataReferenceCollection element. 

#### 9.2.2.8 Status Codes & Error Conditions

#### 9.2.2.9 Response Headers

201 CREATED

204 No Content

### 9.2.3 Delete Service Group
