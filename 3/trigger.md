## Trigger
```
trigger LastName on Contact(after insert){
    if (Trigger.isAfter){
        if (Trigger.isInsert){
            LastNameHelper.deleteContacts(trigger.new);
        }
    }
}
```
