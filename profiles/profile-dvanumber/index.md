---
layout: main
title: SMART on FHIR Profiles (AU) - DVA Number
---

# Profile: Department of Veterans' Affairs (DVA) Number

The Department of Veterans' Affairs (DVA) Number is as reference to eligibility for DVA claiming.

## Context

* DVA Number is relevant to the [Patient](http://www.hl7.org/implement/standards/fhir/patient.html#Patient) resource
* DVA Number is represented as a `Patient.identifier`
* `0 or 1` Department of Veterans' Affairs (DVA) Number may be present

## Description

Each DVA Number is composed of:

* `0 or 1` identifier type description as  `identifier.type`
 * `0 or 1` coded identifier type description as `identifier.type.coding` with `code` = "DV"; `system` = "http://hl7.org.au/fhir/v2/0203"; `display` = "Department of Veterans Affairs Number"
 * `0 or 1` text type description as `identifier.type.text` with fixed `value` = "DVA Number"
* `1` identifier system as `identifier.system` with fixed `value` = "http://ns.electronichealth.net.au/id/hi/dva"
* `1` IHI value as `identifier.value` with `value` 
 
##  XML example
```
<Patient>
    ...
    <identifier>
        
		<!-- "type" optional -->
        <type> 
		
			<!-- "coding" optional -->
            <coding> 
                <system value="http://hl7.org.au/fhir/v2/0203"/>
                <code value="DV"/>
                <display value="Department of Veterans Affairs Number"/>
             </coding>
			 
			 <!-- "text" optional -->
             <text value="DVA Number"/> 
			 
         </type>
		 
		<!-- "system" required : fixed -->
        <system value="http://ns.electronichealth.net.au/id/hi/dva"/>
		
		<!-- "value" required -->
        <value value="N 908030D"/>
         
         
    </identifier>
    ...
</patient>
```
