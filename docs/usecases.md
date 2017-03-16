# 6 Use Cases

This document describes the services provided by Digital Capability Publishers.

The use cases listed in this section are separated in two categories: 

 - Use cases dealing with the actual operation of sending and receiving business documents; and 
 - Use cases dealing with configuration and registration of information to enable the operational use cases. 

## 6.1 Sending a Business Document (including Dynamic Discovery)

![usecase-6.1.Logo](/images/Usecase-6.1.PNG)

## 6.2 Maintenance of Dynamic Discovery Information

![usecase-6.2.Logo](/images/Usecase-6.2.PNG)


## 6.3 Use Case Descriptions

| | | | | |
| ---| ---| ---| -----| -----|
**Use Case ID**| **Actors**| **Description**| **High Level Process**| **Present In**|
SUC002 | Digital Capability Publisher, Access Point, Digital Capability Locator | Register Digital Capability Publisher Alias Address | Maintenance | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
SUC003 | Access Point, Digital Capability Publisher | Register Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
SUC005 | Access Point, Digital Capability Publisher, Digital Capability Locator | Lookup Participant's Digital Capabilities (this includes SUC006) | Sending a business document | Implementation guides for: Digital Capability Locator, Digital Capability Publisher and Access Point |
SUC006 | Access Point, Digital Capability Locator | Lookup Digital Capability Publisher Alias Address |Sending a business document |  Implementation guides for: Access Point and Digital Capability Locator |
SUC013 | Access Point, Digital Capability Publisher, Digital Capability Locator | Remove Digital Capability Publisher Alias Address | Maintenance | Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
SUC014 | Access Point, Digital Capability Publisher | Update Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
SUC015 | Access Point, Digital Capability Publisher | Remove Capability | Maintenance | Implementation guides for: Digital Capability Publisher and Access Point |
BUC033 | Access Point, Digital Capability Publisher, Digital Capability Locator | List of Participant’s Digital Capabilities (Note: looking up all a participant’s capabilities is optional, and could be used by the sender to determine a trading partner’s ability to receive business documents) (this includes SUC006) | Maintenance/ Sending a business document | Implementation guides for: Digital Capability Locator, Digital Capability Publisher and Access Point |
BUC036 | Access Point, Digital Capability Publisher, Digital Capability Locator | Business On-boarding (note: this includes a business new to eInvoicing or a business changing provider) (includes SUC002, SUC003 and SUC014) | eDelivery On-boarding / Maintenance |Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |
BUC100 | Access Point, Digital Capability Publisher, Digital Capability Locator | Send Business Document to Recipient (includes SUC005 – Lookup Participant’s Digital Capability) | Sending a business document |Implementation guides for: Access Point, Digital Capability Publisher and Digital Capability Locator |




