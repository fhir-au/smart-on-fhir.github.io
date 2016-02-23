---
layout: main
title: SMART on FHIR Profiles (AU) - Indigenous Status
---

# Extension: Indigenous Status

Indigenous status is a common patient administration concept in Australian systems. An extension is added to represent this concepts as no FHIR core element is suitable at this time.

## Context

* Indigenous Status is relevant to the [Patient](http://www.hl7.org/implement/standards/fhir/patient.html#Patient) resource
* Indigenous Status is represented as a `Patient.extension`
* `0 or 1` Indigenous Status may be present

## Description

Each Indigenous Status is composed of:

* `1` extension identity as `extension.url` fixed as `http://hl7.org.au/fhir/StructureDefinition/indigenous-status`
* `1` coded indigenous status in `valueCoding` from [Indigenous Status Valueset](http://terminology.hl7.org.au/open/ValueSet/indigenous-status)
 * `1` code in `valueCoding.code.value` as per value set
 * `1` system in `valueCoding.system.value` fixed as `http://meteor.aihw.gov.au/content/index.phtml/itemId/602543#Codes`
 * `1` code in `valueCoding.display.value` as per value set
 
##  XML example
```
<Patient>
    ...
    <extension url="http://hl7.org.au/fhir/StructureDefinition/indigenous-status">
      <valueCoding>
         <code value="1"/>
         <system value="http://meteor.aihw.gov.au/content/index.phtml/itemId/602543#Codes" /> <!- fixed vocab -->
         <display value="Aboriginal but not Torres Strait Islander origin" /> <!--required: indigenous status display name -->
     </valueCoding>
   </extension>
   ...
</Patient>
```
