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
