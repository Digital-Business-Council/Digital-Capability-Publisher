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

a. <<include>> SUC005 – Lookup Participant’s Digital Capability.
4.The sending Access Point sends the business document to the recipient’s nominated Access Point for the business document type; 
5.The receiving Access Point receives the business document successfully; 
6.The receiving Access Point sends the business document to the recipient;
7.The recipient receives the business document from their nominated Access Point successfully; 
8.End flow.
