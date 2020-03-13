# Quick intro for PACT testing

## How to react on new contract

1. <a name="cdct-pbi"></a> Ensure that consumer add appropriate tag to his PBI/task, like: CDCT:<consumer_name>"
2. Ensure that contract is present on pact broker: http://pd-pactbr-1-dk1:9292/
3. Review the contract, identify ``GIVEN`` tag in the contract (this will be your entry point for initializing new tests data)
4. Prepare new [tests data](#adding-new-test-data-for-the-contract)


## Adding new test data for the contract

1. Go to the ``Services.CMS.Data.ContractTests.ProviderStateSetup.StateController``
2. Add new method with ``ProviderState`` attribute and set the state value same as ``GIVE`` state from the consumer contract, for example:  
 Contract has next ``Interactions`` text:
 Given **set of sites and languages has been registered**, upon receiving **returns a set of registered sites and languages**. from shell, with
 You should copy **set of sites and languages has been registered** and add this text to your provider state, like: ``[ProviderState("Set of sites and languages has been registered")]``
 3. Go to the ``Services.CMS.Data\tests\Services.CMS.Data.ContractTests.ProviderStateSetup\TestData`` folder
 4. Using DevEx rules for adding new content to the Sitecore, create new items/templates under appropriate roots.
 5. Change ``Services.CMS.Data\tests\Services.CMS.Data.ContractTests\App.config`` file by adding new tag to the ``TagsToVerify`` application setting. You should set value corresponding to the [consumert PBI](#cdct-pbi) with contract testing.
 6. Create a PR
 7. Notify consumer about your progress. If your PR is green you should complete it and only then consumer can do the same.
