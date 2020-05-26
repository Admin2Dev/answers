## conUpdater Class

```
public class conUpdater {
    public static void updateAccount(String accString, String descString){

        List<Account> accList = [SELECT ID, Name, (SELECT ID, Description FROM Contacts) FROM Account WHERE Name = :accString];

        List<Contact> finalList = new List<Contact>();

        if (accList.size() > 0){
            for(Contact iterator: accList[0].contacts){
                iterator.description = descString;
                finalList.add(iterator);
            }
            update finalList;
        }
        else{
            System.debug('Account does not exist');
        }

    }

}

```
