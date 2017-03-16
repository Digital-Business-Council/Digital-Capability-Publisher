# 8 Identifiers

An endpoint address can be uniquely identified by a combination of: 

 - The business by its participant identifier;
 - THe type of document that is to be transmitted;
 - The process in which the transmission is participating; and
 - The transport protocol used to exchange a message.

## 8.1 Participant Identifier

A participant identifier has two components:

 - The scheme of the identifier; and
 - The unique ID within the scheme.
 
Following the (OASIS, 2010) specification the general structure of a participant identifier is: 

urn:oasis:tc:ebcore:partyid-type:catalog-identifier:scheme-in-catalog::scheme-specific-identifier 

The supported identifier schemes are described in (Digital Business Council, 2016c) and are designed to support national as well as international exchange of business information. 

In an Australian context the use of the Australian Business Number is a valid identifier and the identifier would have the following components: 

Example

urn:oasis:names:tc:ebcore:partyid-type:iso6523:0151::23601120601 

## 8.2 Document Identifier

A document identifier has two components:

 - The scheme of the identifier; and
 - The unique ID within the scheme.
 
The scheme defines the namespace in which the document is specified.
The format as specified in the standard is: 

{identifier scheme}::{rootNamespace}::{documentElementLocalName}[##{Subtype identifier}] 

URL Example:

dbc-docid::urn:www.digitalbusinesscouncil.com.au:dbc:einvoicing:doctype:core-invoice:xsd::core-invoice-1##urn:www.digitalbusinesscouncil.com.au:dbc:einvoicing:process:einvoicing02:ver1.0 

XML Example: 

## 8.3 Process Identifier

A process identifier has two componenets:

 - The scheme of the identifier; and
 - The unique ID within the scheme.
 
XML Example:

## 8.4 Transport Profile

A transport profile has one component

