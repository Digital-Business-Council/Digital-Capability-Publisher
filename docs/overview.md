# 2 Overview

This document describes the services offered by a Digital Capability Publisher. Digital Capability Publishers implement the OASIS Service Metadata Publisher standard (OASIS, 2014). The OASIS SMP standard defines the discovery services required for the dynamic discovery of a recipient’s endpoint.

![dcp-diagram.Logo](/images/DCP-diagram.PNG)

The context diagram Figure 1 shows the components included in the Interoperability Framework and where the Digital Capability Publisher (Digital Capability Publisher) sits. The Digital Capability Publisher is used/accessed by Access Points in the eInvoicing process. 

The Digital Capability Publisher operates in a four-corner model (see Figure2: Four Corner Model). In a four-corner model, the businesses, or participants, that exchange electronic documents use access points to send and receive these documents. Each participant registers their receiving Access Point in a Digital Capability Publisher. The sending Access Point is then able to determine the receiver’s digital address by lookup up a participant’s identifier in the Digital Capability Publisher. This happens in conjunction with a Digital Capability Locator, which stores the Digital Capability Publisher address in association with the participant identifier.

![Fourcorner-model.Logo](/images/Fourcorner-model.png)

The OASIS SMP standard (OASIS, 2014) omits the services required to create, update and delete entries in the Digital Capability Publisher. Implementers are expected to provide an interface to perform these maintenance activities. A web based user interface is one way of providing this interface. 
This document does not go into detail on the user interface as the person interacting with this interface will be able to adapt to different implementations. This document does describe a HTTP API interface, popularly known as a RESTful interface (described in section 0). External parties can use this interface to programmatically maintain business capability information. 
