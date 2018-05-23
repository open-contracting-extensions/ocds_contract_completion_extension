# Contracts Register Extension

The Open Contracting Data Standard can be used to provide information on all stages of a contracting process, from planning through to implementation.

This extension introduces four fields that can be used at the end of a contracting process to provide details of the final date and value of the contract, and, where there is variation, to provide a justification of this. 

## Additional fields

The fields introduced by this extension are:

* **`implementation/endDate`** - The date when contract implementation ended. This should only be provided when contract implementation is complete. Where `implementation/endDate` varies from the anticipated `contract/period/endDate` an explanation of the variance should be provided in `implementation/endDateDetails`.

* **`implementation/endDateDetails`** - Details related to the endDate. This may be a justification for the contract's completion date being different than in the original contract.

* **`implementation/finalValue`** - The total value of all payments for a completed contract. This should only be provided when the final payment has been recorded. If `implementation/transactions` are used for this contract, this field should equal the sum of the `transaction/value/amount` fields. Where `finalValue/amount` varies from `contract/value/amount` an explanation of the variance should be provided in `finalValueDetails`. 

* **`implementation/finalValueDetails`** - Details related to the final value. This may be a justification for the completed contract's value being different than in the original contract.

## Using existing OCDS fields within a Contracts Register

OCDS contains many existing fields that can be used as part of a Contracts Register. These are documented [in the schema reference](http://standard.open-contracting.org/latest/en/schema/reference/). This extension does not modify any of these fields. However, the following list is provided for convenience of those considering the design of a contracts register:

* **Supplier details**  should be recorded within the `awards` section, linked via `contracts/awardID` (even if you are only releasing information at the contract stage, you may provide information in the tender and award sections)
* **Contract documents** can be linked to under `contract/documents`
* **Performance reports** can be provided under `contract/implementation/documents`
* **Details of payments** can be provided under `contract/implementation/transactions`
* **Progress details** can be provided using `contract/implementation/milestones`. 
* **Amendments** can be described using the `contact/amendments` array, and with past values provided using the OCDS [releases model as described here](http://standard.open-contracting.org/latest/en/implementation/amendments/) 

### Using milestones to show contract completion 

Milestones may have a `status` of 'scheduled', 'met', 'notMet' or 'partiallyMet'. By providing at least one milestone for a contract, and then ensuring `milestone/status` is updated when `implementation/endDate` you can indicate whether a contract ended with successful delivery of all milestones and deliverables. 

## JSON and CSV serializations

In some cases, it may be possible to design a simple contracts register using the [flat CSV serialization of OCDS](http://standard.open-contracting.org/latest/en/implementation/serialization/#csv). 

## Example 

ToDo

## Issues

Report issues for this extension in the [ocds-extensions repository](https://github.com/open-contracting/ocds-extensions/issues), putting the extension's name in the issue's title.
