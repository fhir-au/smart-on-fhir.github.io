---
layout: main
title: SMART on FHIR Profiles (AU) - Medicare Number
---

# Profile: Medicare Number

Medicare number is used as reference to eligibility for Medicare claiming.

No distinction is made between temporary and final Medicare Number issuance.

## Context

* Medicare Number is relevant to the [Patient](http://www.hl7.org/implement/standards/fhir/patient.html#Patient) resource
* Medicare Number is represented as a `Patient.identifier`
* `0 or 1` Medicare Number may be present

## Description

Each Medicare Number is composed of:

* `0 or 1` identifier type description as  `identifier.type`
 * `0 or 1` coded identifier type description as `identifier.type.coding` with `code` = "MC"; `system` = "http://hl7.org/fhir/v2/0203"; `display` = "Patient's Medicare Number""
 * `0 or 1` text type description as `identifier.type.text` with fixed `value` = "Medicare Number"
* `1` identifier system as `identifier.system` with fixed `value` = "http://ns.electronichealth.net.au/id/hi/mc"
* `1` Medicare Number value as `identifier.value` with `value` as 10 or 11 digits (optional individual reference number - IRN)
* `0 or 1` expiry date `identifier.period` with `end.value` date yyyy-MM (or yyyy-MM-dd  for temporary issuance)
 
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
                <code value="MC"/>
                <display value="Patient's Medicare Number"/>
            </coding>
			
			<!-- "text" optional -->
            <text value="Medicare Number"/> 
			
        </type>
		
		<!-- "system" required and fixed -->
        <system value="http://ns.electronichealth.net.au/id/hi/mc"/>
		
		<!-- "value" required: 10 or 11 digits -->
        <value value="32788511952"/> 
		
		<!-- optional:  may be yyyy-MM or yyyy-MM-dd -->
        <period> 
            <end value="2017-03"/>
        </period>
		
        <!-- "assigner" optional -->
    </identifier>
    ...
</Patient>
```
