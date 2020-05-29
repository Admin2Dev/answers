## NameChanger Batch Class

```
global class NameChanger implements Database.Batchable<sObject> {
    global Database.QueryLocator start(Database.BatchableContext bc) {
        // collect the batches of records or objects to be passed to execute

        return Database.getQueryLocator('SELECT Id, LastName FROM Contact WHERE LastName = \'Test\' OR LastName = \'Test 2\' '); //Use the OR operator to get both Test and Test 2 values.
    }
    global void execute(Database.BatchableContext bc, List<Contact> conList){
        //Process records

        List<Contact> finalList = new List<Contact>();

        for (Contact iterator: conList){
            if (iterator.LastName == 'Test'){ //Check for lastName
                iterator.FirstName = 'Batch Test';
            }
            else { //If lastName isn't Test, it's Test 2 because that's what the SOQL Query calls for
                iterator.FirstName = 'Batch Test 2';
            }

            finalList.add(iterator);
        }

        update finalList;


    }
    global void finish(Database.BatchableContext bc){
        // execute any post-processing operations
    }
}
```
