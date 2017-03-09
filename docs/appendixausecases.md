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

1.The Sender populates the business document with the required information (identifier and scheme, document type and process);

2.The Sender sends the business document to their Access Point;

3.The sending Access Point performs the business discovery process to obtain the capability of the recipient (which includes obtaining the service endpoint of the receiving Access Point); 
 - a. <<include>> SUC005 – Lookup Participant’s Digital Capability.

4.The sending Access Point sends the business document to the recipient’s nominated Access Point for the business document type;

5.The receiving Access Point receives the business document successfully;

6.The receiving Access Point sends the business document to the recipient;

7.The recipient receives the business document from their nominated Access Point successfully;

8.End flow.

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

1. The requester establishes the location of the recipient’s digital capabilities;

   a. <<include>> SUC006 - Lookup Participant’s DCP Alias Address; 

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
 
 d. The business has Access Point and Digital Capability Publisher services with separate providers and consolidates the services in one     provider.
 
 e. The business has different Service Providers for Digital Capability Publisher and Access Point services, and moves each service to       two new Service Providers. 
