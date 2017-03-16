# 7 Service Metadata Publishing (SMP) Version 1.0 Profile (Normative)\

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
