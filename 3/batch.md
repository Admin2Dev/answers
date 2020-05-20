## Batch Class

```
global class batchDeleter implements Database.Batchable<sObject> {

    global Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator('SELECT Id, LastName FROM Contact WHERE LastName LIKE \'Test%\'');
    }

    global void execute(Database.BatchableContext bc, List<sObject> deleteList){
        delete deleteList;
    }
    global void finish(Database.BatchableContext bc){
        List<Contact> con = [SELECT Id, LastName FROM Contact WHERE LastName = 'DeleteBatch' LIMIT 1];
        List<Contact> finalList = new List<Contact>();
        for (Contact iterator: con){
            iterator.Description = 'Deleted records with ID ' + bc.getJobId();
            finalList.add(iterator);
        }
        update finalList;

    }
}
```
