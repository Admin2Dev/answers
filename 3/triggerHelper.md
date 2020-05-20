## Trigger Helper
```
public class LastNameHelper{

    public static void deleteContacts(List<Contact> newList){

        for(Contact iterator: newList){
            if (iterator.LastName == 'DeleteBatch'){
                batchDeleter runBatch = new batchDeleter();
                Database.executeBatch(runBatch);

            }
        }

    }
}
```
