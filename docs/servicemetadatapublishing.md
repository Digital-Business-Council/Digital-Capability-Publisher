# 7 Service Metadata Publishing (SMP) Version 1.0 Profile (Normative)

This section explains how the OASIS BDX-smp specification (OASIS, 2014) is profiled for use within the Interoperability Framework.

The BDX-smp specification defines a data model and a REST binding to retrieve service metadata:

 - A Capability Publisher hosts metadata for each participant identifier at a predefined URL; and
 - The sender uses this URL in a HTTP GET operation which returns the metadata relating to that recipient's capabilities.

![capability-lookup.Logo](/images/Capability-lookup.PNG)

The sender retrieves the information necessary for setting up an interoperability process. The Capability Publisher stores the capability metadata, which enables routing of documents received from a sender to the correct recipient. Capability metadata is a combination of information on the end entity recipient (its identifier, supported business documents and processes in which it accepts those documents) and the access point (metadata which includes technical configuration information on the receiving endpoint, such as the transport protocol and its address). 
Each participant identifier MUST be registered in only one Digital Capability Publisher (an organization may have more than one participant identifier). 
BDX-Location provides the underlying standard for the Digital Capability Locator described in the Digital Business Council Digital Capability Locator Implementation Guide (Digital Business Council, 2016a) . The digital address for a Capability Publisher is mapped to a participant identifier in the Digital Capability Locator.

## 7.1 Data Model
### 7.1.1 Signed Service Metadata

The signed service metadata data structure contains the actual business capability. This structure is adopted from the standard as-is except for the redirect element which MUST NOT be used.

![signed-service-metadata.Logo](/images/Signed-service-metadata.PNG)

The location of a signed service metadata document depends on the following identifiers:

 1. Participant identifier: identifies the business offering the capability; and
 2. Document identifier: identifies the document that is being transmitted;

These two identifiers are required to return a capability record which may include a list of processes. To determine the correct process, the client needs to know the Process identifier. Each process defines a list of endpoints which are identified by a transport profile. 
These identifiers are related to information in the messaging protocol as specified in the Digital Business Council Access Point Implementation Guide (Digital Business Council, 2016b) and are profiled for use in the Interoperability Framework (See also sections 7.2, 7.3 and 7.4). 

### 7.1.2 Service Group

The service group data structure contains a list of capabilities for a business. A Capability Publisher MUST support the service group resource location. 

![service-group.Logo](/images/Service-group.PNG)

Each Service Metadata Reference is a hyperlink to a Signed Service Metadata resource. 

## 7.2 Signature Specification

The signature MUST follow the standard described in (OASIS, 2014) section 3.6.2.

## 7.3 Participant Identifier

The participant identifier is based on the ebCore Party-ID standard (OASIS, 2010) and is profiled by the Digital Business Council (Digital Business Council, 2016c). Actual values will be defined in the implementation section of this document.

## 7.4 Document Identifier

Document Identifiers are described in the BDX-smp standard (OASIS, 2014, p. 16). Actual values will be defined in this implementation guide. 

## 7.5 Process Identifier

Process Identifiers are described in the BDX-smp standard (OASIS, 2014, p. 18). Actual values will be defined in this implementation guide. 

## 7.6 Discovery Interface

The Capability Publisher REST interface provides access to two resources:

 1. Signed Service Metadata: the representation is an XML document with a service metadata and signature; and
 2. Service Group: the representation is an XML document with a list of locations for signed service metadata resources.
 Representation of these two resources is per the BDX-smp standard. 
 
The management interface concerned with updates and changes to the Capability Publisher are described further in this implementation guide.

### 7.6.1 Location of Signed Service Metadata

The resource address of the Signed Service Metadata follows the BDX-smp standard:

Actual values depend on the scheme identifier and document identifier types. These values will be published further in this implementation guide.

### 7.6.2 Location of Service Group

The resource address of the Service Group is: 

Actual values depend on the scheme identifier. This value is described further in this implementation guide. 
