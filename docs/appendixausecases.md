# APPENDIX A: Use Cases
## BUC100 Send Business Document to Recipient
**Purpose**

This high level use case describes the end to end process of sending a business document to a recipient. 

**Assumptions**

N/A

**Preconditions**

 1. The Sender, Recipient, Capability Publisher and the Access Points are participants in eDelivery. 

**Post conditions**

 1. The recipient receives the Sender’s business document successfully. 

**Basic Flow**

 1. The Sender populates the business document with the required information (identifier and scheme, document type and process);

 2. The Sender sends the business document to their Access Point;

 3. The sending Access Point performs the business discovery process to obtain the capability of the recipient (which includes obtaining the service endpoint of the receiving Access Point); a. <<include>> SUC005 – Lookup Participant’s Digital Capability.

 4. The sending Access Point sends the business document to the recipient’s nominated Access Point for the business document type;

 5. The receiving Access Point receives the business document successfully;

 6. The receiving Access Point sends the business document to the recipient;

 7. The recipient receives the business document from their nominated Access Point successfully;

 8. End flow.

## BUC033 List Participant's Capabilities

**Purpose**
This use case describes the steps required for a party, possibly a sender, to discover the entire capabilities (ie every process) supported by a participant. 

This use case is optional as it would only be useful if there were more than one process supported by a participant. It is not necessary for a Sender to discover all capabilities of a Recipient to send a business document from corners 1 to 4. 

**Assumptions**

 1. Any party, even those not participating in eDelivery, can view a Participant’s Capabilities. 

 2. No authentication or authorisation checks are required.

**Pre-conditions**

 1. The requester needs to know the identifier of the participant they are looking up.

**Post-conditions**

 1. The recipient's digital capabilities have been determined by a participant.

**Basic Flow**

 1. The requester establishes the location of the recipient’s digital capabilities;  a. <<include>> SUC006 - Lookup Participant’s DCP Alias Address; 

 2. The requester constructs the request to retrieve a recipient’s capability list;

 3. The requester sends the request to the recipient’s Digital Capability Publisher;

 4. The Digital Capability Publisher creates the response including the capabilities for each process the participant has in their capability record;

 5. The requester receives the response;

 6. End flow. 

## BUC036 Business On-boarding

**Purpose**
This use case describes the process to on-board a business to a single Digital Capability Publisher and/or one or more Access Point services for eDelivery. This does not include Access Point and Digital Capability Publisher service providers themselves, who are covered by the process described in BUC010 – Service Provider On-Boarding.

There are a number of scenarios covered by this use case:

 1. A business is entering the eDelivery framework for the first time (new participant).
 
 2. A business changes their service provider(s) to a single or multiple service provider (noting a business can only have one and only one Digital Capability Publisher service provider): 

     a. The business moves both services from one service provider to one or more service providers.
 
     b. The business moves only their Access Point service for a particular process to a new service provider.
     
     c. The business moves only the Digital Capability Publisher service to a new service provider.
     
     d. The business has Access Point and Digital Capability Publisher services with separate providers and consolidates the services in one provider. 
     
     e. The business has different Service Providers for Digital Capability Publisher and Access Point services, and moves each service to two new Service Providers. 
 
 **Assumptions**
 
 1. A Service Provider can operate an Access Point and/or a Digital Capability Register but it is not mandatory to provide both. 
 
 2. Where a Service Provider can provide both services, whether a business chooses to use both services of that one service provider is completely at their discretion. 

**Constraints**

 1. The Service Provider, when providing both services, must create and maintain the business’ Digital Capability Locator entry and Digital Capability Publisher capability record. 
 
 2. When the business enters into agreements with a Digital Capability Publisher service provider and one or more Access Point service providers, the Digital Capability Publisher Service provider is responsible for coordinating, creating and maintaining the Digital Capability Locator entry and Digital Capability Publisher record on behalf of the business for the duration of this arrangement as it will need all Access Point details to create the business’ Capability record in their nominated Digital Capability Publisher. 
 
 3. When the business has its own Access Point, the Service Provider for Digital Capability Publisher services is responsible for creating and maintaining the Digital Capability Locator entry, creating the capability record and responding to requests by the business to update the Access Point details the business uses as required. 
 
 4. In Access Point service provider change events, The Service Provider holding the business’ capability record must comply with Access Point Service Provider request to update the capability record with the new Access Point details. 
 
 5. As defined in the Council provider agreements, the losing Service Provider must cooperate with the gaining (New) Service Provider during portability/change of service events.
 
 6. Only one capability record can exist in the eDelivery framework for a participant; this record contains all the capabilities of the business. 
 
 **Pre-conditions**
 
 1. The business has agreements with one or more Service Providers for receiving Council supported business processes and documents through one or more Access Point providers and only one Digital Capability Publisher provider, having either become a new participant or changed service providers.
 
 2. The business has only one capability record in any accredited Digital Capability Publisher.
 
 3. The business is discoverable in the Digital Capability Locator and, if the new Digital Capability Publisher is listed in the Digital Capability Locator entry. 

**Post-conditions**

 1. The business has agreements with one or more Service Providers for receiving Council supported business processes and documents through one or more Access Point providers and only one Digital Capability Publisher provider, having either become a new participant or changed service providers.
 
 2. The business has only one capability record in any accredited Digital Capability Publisher.
 
 3. The business is discoverable in the Digital Capability Locator and, if the new Digital Capability Publisher is listed in the Digital Capability Locator entry. 
 
 **Basic FLow- New Participant in eInvoicing; Business chooses to use a single Service Provider for both Access Point and Digital Capability Publisher services**
 
 1. The business determines their requirements; 
 2. The business investigates the services offered and pricing of various service providers;
 3. The business determines the Service Provider(s) that meets their requirements;
 4. The business enters an agreement with the New Service Provider;
 5. The New Service Provider determines if the business’ capability is already registered in a capability register (this also determines if the client has an Access Point service in the framework also); 
 6. The business does not have an existing capability record registered and requires it to be created in the New Service Provider’s Digital Capability Publisher; 
 7. The New Service Provider determines the client does not have an Access Point service and will use the New Service Provider’s AP; 
 8. The New Service Provider adds its own supported Access Point address, transport profiles, document types and processes to the business’ capability record in its own Digital Capability Publisher; a. <<include>> SUC003 – Register Capability. 
 9. The New Service Provider requests the capability address (Digital Capability Locator entry) be added to the Digital Capability Locator; a. <<include>> SUC002 – Register Capability Address. 
 10. The New Service Provider informs the business the on-boarding activities have been completed;
 11. End flow. 

**Alternate Flows**

 **1. New Participant; Business is signing up to Digital Capability Publisher service only (participant may have an Access Point of its own or is signing a separate agreement with a different Access Point Service Provider).**

     a. At step 6, the New Service Provider determines the Business is entering into an agreement with a different Access Point service provider or is using its own Access Point;
  
     b. The New Service Provider obtains the Access Point endpoint address and transport profile it supports for each document and process, from either the Business (if using its own AP) or the Business’ Access Point Service Provider(s);
     
     c. The New Service Provider creates a capability record including Access Point endpoint address, transport profile, document and process types;  i. <<include>> SUC003 – Register Capability. 
     
     d. Resume at step 9. 

**2. Existing Participant; Business has an existing Digital Capability Publisher service and is changing only this service to the New Service Provider.**

At step 6, the New Service Provider discovers the business has an existing Digital Capability Publisher service that needs to be changed to the New Service Provider’s Digital Capability Publisher service.

     a. The New Service Provider informs the Losing Digital Capability Publisher Provider they are now providing the business’ Digital Capability Publisher service.
     
     b. The Losing Digital Capability Publisher Provider deprecates the business’ capability record in their Digital Capability Publisher.
     
     c. The New Service Provider contacts the business’ existing Access Point Provider(s) to confirm the Access Point endpoint address and supported transport profile for each document type and process (the New Service Provider would have obtained this information when looking up the business’ capability record in step 5 of the basic flow).
     
     d. The New Service Provider creates a capability record including Access Point endpoint address, transport profile, document types and process types. i. <<include>> SUC003 – Register Capability 
     
     e. Resume at step 9. 

**3. Exisiting Participant; the business is moving both services to the New Service Provider.**

At step 6, the New Service Provider discovers the business has an existing Digital Capability Publisher service that needs to be changed to the New Service Provider’s Digital Capability Publisher service.

     a. The New Service Provider informs the Losing Digital Capability Publisher Provider they are now providing the business’ Digital Capability Publisher service.
     
     b. The Losing Digital Capability Publisher Provider deprecates the business’ capability record in their Digital Capability Publisher.
     
     c. The New Service Provider informs the previous Access Point Provider they are the business’ nominated Access Point Provider.
     
     d. The New Service Provider creates a capability record including the Access Point endpoint address(es), transport profile(s), document and process types. i. <<include>> SUC003 – Register Capability 
     
     e. Resume at step 9. 

**Exception flows**

 **1. New Participant; Business is signing up to Access Point service with the New Service Provider, it will use another Service Provider for Digital Capability Publisher services.**

At step 6, the New Service Provider determines the business will use a different service provider for a Digital Capability Publisher service.

     a. The Digital Capability Publisher service provide requests the New Service Provider’s Access Point details; 
 
     b. The New Service Provider provides their Access Point endpoint address and transport profile, to enable the Digital Capability Publisher Service Provider to successfully create the business’ capability record;
 
     c. The Digital Capability Publisher Service Provider creates the capability record; i. <<include>> SUC003 – Register Capability. 
  
     d. The Digital Capability Publisher Provider requests addition of the business’ Digital Capability Locator entry in the Digital Capability Locator;  i. <<include>> SUC002 – Register Capability Address. 
  
     e. The Digital Capability Publisher Provider informs the business that all access points have been added to the capability record for each document/process and the Digital Capability Locator entry has been created; 
  
     f. End flow. 
  
  **2. Exisiting Participant: THe Business is changing only to a new Access Point Service Provider for a particular document type and process.**
  
At step 9, the service provider discovers the participant has an existing Access Point provider and will be providing this service for the business instead, however the business is retaining its current Digital Capability Publisher Service provider.

     a. The New Service Provider informs the previous Access Point service provider they are the business’ new Access Point provider for the particular document type and process; 
     
     b. The New Service Provider looks up the holder of the business’ capability record;
     
     c. The New Service Provider provides their Access Point endpoint address and accepted transport protocol for the process and document type to the Digital Capability Publisher Provider to successfully create the business’ capability record; 
     
     d. The Digital Capability Publisher Provider updates the capability record; i. <<includes>> SUC014 – Update Capability. 
     
     e. The Digital Capability Publisher Provider informs the business their change in Access Point service has been updated and they are able to receive documents through the new Access Point;
     
     f. End flow. 
 
 ## SUC002 Register Digital Capability Publisher Alias Address
 
 **Purpose**
 
This use case describes the interaction required for the Identifier to be mapped to the Digital Capability Publisher Alias Address of a participant’s Digital Capability Publisher and this mapping added to the Digital Capability Locator, enabling the Participant to be discovered. 

**Assumptions**

N/A

**Pre-conditions**

 1. The participant’s capability record has been added to an accredited Digital Capability Publisher. 
 2. The participant does not have a Digital Capability Publisher Alias Address already registered. 
 3. The Digital Capability Publisher has been accredited by the council and added to the Digital Capability Locator. 
 4. The Digital Capability Publisher has obtained the identifier and the identifier scheme of the participant. 
 
**Post-conditions**

 1. The Digital Capability Publisher Alias Address of the participant’s Digital Capability Publisher has been added to the Digital Capability Locator, with the Participant’s identifier mapped to the Digital Capability Publisher endpoint address. 
 2. The participant’s Digital Capability Publisher address is discoverable on the Digital Capability Locator. 
 
**Basic Flow**

 1. The requester constructs the Digital Capability Publisher Alias Address record addition request;
 2. The requester sends the Digital Capability Publisher Alias Address record addition request to the Digital Capability Locator;
 3. The Digital Capability Locator receives the Digital Capability Publisher Alias Address record addition request;
 4. The Digital Capability Locator checks the requester is authorised to request a record addition; 
 5. The Digital Capability Locator verifies the Digital Capability Publisher Alias Address record addition request is in the correct format; 
 6. The Digital Capability Locator determines no record exists for this participant;
 7. The Digital Capability Locator locates the accredited Digital Capability Publisher specified in the request for inclusion in the participant’s record;
 8. The Digital Capability Locator checks the Digital Capability Publisher in the request is accredited;
 9. The Digital Capability Locator publishes the participant’s Digital Capability Publisher Alias Address record;
 10. The Digital Capability Locator responds, informing the requester that the Digital Capability Publisher Alias Address has been published successfully; 
 11. End flow.
 
 **Exception Flows**
 1. At step 4, the Digital Capability Locator determines the requester is not authorised and sends an error response indicating this; 
 
 2. At step 5, the Digital Capability Locator is unable to add the Digital Capability Publisher Alias Address record successfully because the request format is invalid;
 
    a. The Digital Capability Locator sends an error message response to the requester;
  
    b. End flow.
  
 3. At step 6, the Digital Capability Locator is unable to add the Digital Capability Publisher Alias Address record successfully to the Digital Capability Locator because the participant already has a record;
 
    a. The Digital Capability Locator sends an error message response to the requester;
  
    b. End flow.
  
 4. At step 7, the Digital Capability Locator is unable to add the Digital Capability Publisher Alias Address record successfully because the Digital Capability Publisher identifier provided cannot be found;
 
    a. The Digital Capability Locator sends an error message response to the requester;
  
    b. End flow.
  
 5. At step 8, the Digital Capability Locator is unable to add the Digital Capability Publisher Alias Address record successfully because the Digital Capability Publisher is not accredited;
 
    a. The Digital Capability Locator sends an error message response to the requester;
  
    b. End flow.
  
  ##SUC006 Lookup Digital Capability Publisher Alias Address
  
  **Purpose**
This use case describes the steps required for a party to discover the Digital Capability Publisher Alias Address of a participant. 

**Assumptions**

 1. The Digital Capability Locator does not supply the URL to the capability record in the Digital Capability Publisher, but only the URL of the Digital Capability Publisher, it is up to the requester to construct the location of the capability record URL in the subsequent request.
 2. The business document may have been generated by the sender and sent to the access point as part of sending a business document. The Access Point may be trying to discover the location of the capability record in order to send the business document to the recipient’s access point.
 3. Any participant can look up the Digital Capability Publisher Alias Address of another participant.
 
 **Pre-conditions**
 
 1. The requester and Digital Capability Publisher are participants in eDelivery.
 2. The requester is aware of the identifier and the identifier scheme of the participant in order to lookup the Digital Capability Publisher Alias Address.
  
 **Post-conditions**
 1. The location of the recipient’s Digital Capability Publisher endpoint address has been determined by the requester.
  
 **Basic Flow**
 
 1. The requester forms a query to locate the capability record of the recipient;
 2. The requester sends the query to their Domain Name System (DNS) server;
 3. The Digital Capability Locator receives the query;
 4. The Digital Capability Locator locates the Digital Capability Publisher Alias Address for the recipient;
 5. The Digital Capability Locator sends the query response to the requester;
 6. The requester successfully receives the query response;
 7. End flow.
  
**Alternate Flows**

 1. At step 3, the Digital Capability Locator is unavailable at the time of the query;
  a. The requester retries a specified amount of attempts;
  b. The Digital Capability Locator is available during one of the attempts;
  c. Resume at step 3.

 2. At step 2, the Digital Capability Publisher Alias Address of a recipient’s capability has been previously looked up by the requester, stored locally and is still valid (the Time-To-Life has not expired). The capability location is then determined by the requester based on this cached record and the Digital Capability Locator does not need to be queried. 
 
**Exception Flows**

 1. At step 4 the Digital Capability Locator cannot locate the recipient’s Digital Capability Publisher Alias Address record and responds with an error message indicating this outcome;
 2. At step 2 the Digital Capability Locator domain is incorrect;
  
  a. The DNS server responds with an error;
  
  b. End flow.

 3. At step 6 the Digital Capability Publisher Alias Address is not present in the Digital Capability Publisher Alias Address record;
 
  a. The Digital Capability Locator responds to the query; 

  b. The requester receives the response but cannot discover the location of the Participant’s Digital Capability Publisher;
  
  c. End flow.
  
 ## SUC013 Remove Digital Capability Publisher Alias Address

**Purpose**

This use case describes the steps to remove a Digital Capability Publisher Alias Address record from the Digital Capability Locator.

**Assumptions**

 1. The participant no longer trades or decides not to participate in eDelivery.
 2. The Digital Capability Publisher or the participant can request removal the participant’s Digital Capability Publisher Alias Address, so long as they can be authenticated and their permissions allow this.
 3. The requester could be removing the record before adding a new one.
 
**Pre-conditions**

 1. The participant has an existing Digital Capability Publisher Alias Address record.
 
**Post-conditions**

 1. The participant’s Digital Capability Publisher Alias Address record is no longer discoverable on the Digital Capability Locator.
 
**Basic Flow**

 1. The Digital Capability Publisher or participant itself sends a request to the Digital Capability Locator to remove the participant’s Digital Capability Publisher Alias Address record;
 2. The Digital Capability Locator receives the request;
 3. The Digital Capability Locator checks the requester is authorised to request the record to be removed;
 4. The Digital Capability Locator checks the request format is correct;
 5. The Digital Capability Locator locates the participant’s record;
 6. The Digital Capability Locator removes the participant’s Digital Capability Publisher Alias Address record;
 7. The Digital Capability Locator sends a response to the requester confirming the location has been removed;
 8. End flow.
 
**Exception Flows**

 1. At step 3, the Digital Capability Locator determines the requester is not authorised to perform a removal of the Digital Address;
 2. At step 4, the Digital Capability Locator is unable to remove the Digital Capability Publisher Alias Address record successfully because the request format is not valid;
 
  a. The Digital Capability Locator sends an error message response to the requester;
  
  b. End flow.
  
 3. At step 5, the Digital Capability Locator cannot find a Digital Capability Publisher Alias Address Record for the participant;
 
  a. The Digital Capability Locator sends an error message response to the requester;
  
  b. End flow.

## SUC018 List of Accredited Access Points

**Purpose**

This may be performed when a requester wants to discover all accredited Access Points accredited or determine the accreditation status of a particular Access Point.

**Assumptions**

 1. This list will be readily available and not require authentication and authorisation checks for requesters.

**Pre-conditions**

 1. The Access Points on the list have been accredited by the accreditation body.
 
**Post-conditions**

 1. The requester has obtained the list of accredited access points.
 
 **Basic Flow**
 
  1. The requester sends a request to the Digital Capability Locator for a list of accredited access points;
  2. The Digital Capability Locator receives the request;
  3. The Digital Capability Locator compiles the list of accredited Access Points;
  4. The Digital Capability Locator sends the response with the list to the requester;
  5. End flow.
  
## SUC005 Lookup Participant's Digital Capability

**Purpose**

This use case describes the steps required for a party to discover a specific capability for a particular document and process. The party would discover in the capability the service endpoint and transport Profile for a recipient’s Access Point for the specified document and process. 
For example, an Access Point could be trying to determine if the Recipient actually accepts eInvoicing process documents such as Tax Invoices, where to send them and in what format.

**Assumptions**

 1. Capability records should not be cached or stored outside of a Digital Capability Publisher, but the capability looked up in the Digital Capability Publisher each time needs to be discovered.
 
 2. Any party can determined the business processes and capability of a participant in eDelivery without being authenticated or authorised. 

**Pre-conditions**

 1. The requester has obtained the Participant’s identifier and its scheme, the document type, and the business process.
 
**Post-conditions**

 1. The recipient’s digital capability for the document type and business process has been confirmed by a requester.
 2. The requester has determined the recipient’s Access Point endpoint address and transport Profile needed to send the business document.
 
**Basic Flow**

 1. The requester establishes the location of the recipient’s Digital Capability Publisher; 

a. <<include>> SUC006 - Lookup Participant’s DCP Alias Address. 

 2. The requester constructs the request to retrieve recipient’s capability record including participant identifier, document type and process type;
 3. The requester sends the request to the Digital Capability Publisher endpoint;
 4. The Digital Capability Publisher receives the request and verifies the format is correct;
 5. The Digital Capability Publisher finds the appropriate capability record;
 6. The Digital Capability Publisher creates the response including the capability record of the Participant, containing the Access Point service endpoint and transport Profile for the specified process;
 7. The Digital Capability Publisher sends the response to the requester;
 8. The requester receives the response successfully; 
 9 . End flow.
 
**Exception Flows**

 1. At step 5, the Digital Capability Publisher cannot find a Capability Record for the participant;
 
 a. The Capability Record sends an error message response to the requester;
 
 b. End flow. 

 2. At step 2, the Digital Capability Publisher is unable to find the Capability record successfully because the request format is not valid;
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  
  b. End flow.
  
 3. At step 2, the Digital Capability Publisher is unable to find the Capability record successfully because the identifier provided does not conform to an Identifier scheme supported by the Council;
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  
  b. End flow.
  
 4. At step 2, the Digital Capability Publisher is unable to find the Capability successfully because the document type or process provided in the request does not conform to any in the capability record for that participant; 
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  
  b. End flow.
  
## SUC003 Register Capability
 
**Purpose**

This use case describes the steps required for an Access Point provider or a participant to add the digital capability record for the participant on a Digital Capability Publisher. 

**Assumptions**

 1. The party adding the capability record is authenticated and authorised to perform the addition of a capability record on behalf of the Participant.
 
**Pre-conditions**

 1.The Access Point endpoint address and transport Profile for each of the Participant’s supported business processes is known to the party adding the capability record. 
 2. A participant cannot have an existing capability in any Digital Capability Publisher.
 
**Post-conditions**

 1. The participant’s capability record has been added to a Digital Capability Publisher, including the Access Point endpoint address for each business process and the transport Profile used for each process.
 2. There is only one Digital Capability Publisher record for a participant in any Digital Capability Publisher.
 
**Basic Flow**

 1. The Access Point provider or Participant sends the capability record addition request to the Digital Capability Publisher;
 2. The Digital Capability Publisher checks the requester is authorised to perform the addition of a capability record;
 3. The Digital Capability Publisher checks the request format is correct;
 4. The Digital Capability Publisher checks the participant does not have an existing record in this Digital Capability Publisher;
 5. The Digital Capability Publisher creates the capability record;
 6. The Digital Capability Publisher adds the capability record successfully;
 7. The Digital Capability Publisher informs the requester of the successful addition of the record;
 8. The Digital Capability Publisher adds the DCP Alias Address of the participant to the Digital Capability Locator; 

a. <<include>> SUC002 - Register DCP Alias Address. 

 9. End flow.
 
**Exception Flows**

 1. At step 2, the Digital Capability Publisher is unable to add the Capability Record because the requester is not authorised to add a record; 
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  b. End flow.
  
 4. At step 5, the Digital Capability Publisher is unable to add the Capability record successfully because the identifier provided does not conform to an Identifier scheme supported by the Council;
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  b. End flow.
 
 5. At step 5, the Digital Capability Publisher is unable to add the Capability Record successfully because the document identifier in the request does not conform to a supported document identifier scheme;
 
  a. The Digital Capability Publisher sends an error message response to the requester;
  b. End flow.
  
## SUC014 Update Capability

**Purpose**

This use case describes the steps to update a participant’s capability. This could be, for example, to change Access Point endpoint locations for a business process in the capability record, update a transport Profile for a process, or add a capability for a new business process.

**Assumptions**

 1. The Access Point or Participant can update the Digital Capability Publisher.
 2. The requester needs to be authenticated and only authorised parties can update capability records. 

**Pre-conditions**

 1. The participant has an existing capability record in the Digital Capability Publisher.
 
**Post-conditions**

 1. The participant’s capability record has had the appropriate detail updated.
 
**Basic Flow**

 1. The requester sends a request to the Digital Capability Publisher to update the capability record with the appropriate detail;
 2. The Digital Capability Publisher checks if the requester is authorised to an update to the participant’s record;
 3. The Digital Capability Publisher determines the request format to be valid;
 4. The Digital Capability Publisher locates the record to be updated;
 5. The capability record is updated by the Digital Capability Publisher with the requested detail;
 6. The Digital Capability Publisher responds with confirmation the capability record has been updated;
 7. End basic flow.
 
**Exception Flows**

 1. At step 2, the Digital Capability Publisher is unable to add the Capability Record because the requester is not authorised to add a record; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow. 

 2. At step 4, the Digital Capability Publisher cannot find a record belonging to the participant; 

a. The Digital Capability Publisher responds with an error message; 

b. End flow.

 3. At step 3, the Digital Capability Publisher is unable to update the Capability Record successfully because the transport Profile in the request does not conform to the supported Council transport Profiles; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 4. At step 3, the Digital Capability Publisher is unable to update the Capability record successfully because the request format is not valid; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 5. At step 3, the Digital Capability Publisher is unable to update the Capability record successfully because the participant identifier provided does not conform to an Identifier scheme supported by the Council; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 6. At step 3, the Digital Capability Publisher is unable to update the Capability record successfully because the Access Point endpoint address provided does not conform to the correct format; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 7. At step 3, the Digital Capability Publisher is unable to update the Capability Record successfully because the document identifier in the request does not conform to a supported document identifier scheme; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 8. At step 3, the Digital Capability Publisher is unable to update the Capability Record successfully because the process identifier in the request does not conform to a supported process identifier scheme; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

## SUC015 Remove Capability

**Purpose**

This use case describes the steps to remove a participant’s capability. This could be to either remove a single business process from the participant’s record or to remove the entire capability for all business processes for a participant.

**Assumptions**

 1. A requester could be the Access Point or the Participant themselves.
 2. The requester needs to be authenticated and only authorised parties can remove capability.
 
**Pre-conditions**

 1. The participant has an existing capability record in the Digital Capability Publisher.
 
**Post-conditions**

 1. The participant’s capability record has had the appropriate detail(s) removed.
 
**Basic Flow**

 1. The requester sends a request to the Digital Capability Publisher to remove the required capability;
 2. The Digital Capability Publisher checks that the requester is authorised to remove the capability;
 3. The Digital Capability Publisher determines the remove request format to be correct;
 4. The Digital Capability Publisher locates the capability needing to be removed;
 5. The Capability requested by the requester is removed by the Digital Capability Publisher;
 6. The Digital Capability Publisher responds to the requester with confirmation the capability has been removed;
 7. End flow.
 
**Exception Flows**

 1. At step 2, the Digital Capability Publisher is unable to remove the capability because the requester is not authorised to add a record; 

a. The Digital Capability Publisher sends an error message response to the requester; 

b. End flow.

 2. At step 4 the Digital Capability Publisher cannot find a record belong to the participant; 

a. The Digital Capability Publisher responds with an error message; 

b. End flow.

 3. At step 3 the Digital Capability Publisher finds the request format to be invalid; 

a. The Digital Capability Publisher responds with an error message; 

b. End flow. 
