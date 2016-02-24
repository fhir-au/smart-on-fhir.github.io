---
layout: main
title: SMART on FHIR Profiles (AU) - IHI
---

# Profile: Individual Healthcare Identifier (IHI)

The Individual Healthcare Identifier (IHI) is the national identifier for individuals that are the subject of healthcare services.

## Context

* IHI is relevant to the [Patient](http://www.hl7.org/implement/standards/fhir/patient.html#Patient) resource
* IHI is represented as a `Patient.identifier`
* `0 or 1` Individual Healthcare Identifier (IHI) may be present

## Description

Each IHI is composed of:

* `0 or 1` identifier type description as  `identifier.type`
 * `0 or 1` coded identifier type description as `identifier.type.coding` with `code` = "NI"; `system` = "http://hl7.org/fhir/v2/0203"; `display` = "National unique individual identifier"
 * `0 or 1` text type description as `identifier.type.text` with fixed `value` = "IHI"
* `1` identifier system as `identifier.system` with fixed `value` = "http://ns.electronichealth.net.au/id/hi/ihi/1.0"
* `1` IHI value as `identifier.value` with `value` as 16 digit IHI; with prefix "80060"; and valid with Luhn check digit
 
##  XML example
```
<Patient>
    ...
    <identifier>
        <!-- "use" optional: values based on context of use -->
		
		<!-- "type" optional:  the type (and text) is recommended to make display easier -->
        <type> 
			<!-- "coding" optional -->
            <coding> 
                <system value="http://hl7.org/fhir/v2/0203"/>
                <code value="NI"/>
                <display value="National unique individual identifier"/>
            </coding>
			
			<!-- "text" optional -->
            <text value="IHI"/> 
        </type>
		
		<!-- "system" required: fixed -->
        <system value="http://ns.electronichealth.net.au/id/hi/ihi/1.0"/>
		
		<!-- "value" required -->
        <value value="8003608166690503"/>
		
        <!-- "period" optional: values based on context of use -->
		
        <!-- "assigner" optional -->
    </identifier>
    ...
</Patient>
```
