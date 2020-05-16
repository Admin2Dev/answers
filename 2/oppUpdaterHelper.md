# oppUpdaterHelper

```
public class oppUpdaterHelper{

    public static void oppInsertTask(List<Opportunity> oppList){

        List<Task> finalList = new List<Task>();

        for (Opportunity iterator: oppList){
            Task newTask = new Task();
            newTask.WhatId = iterator.id;
            newTask.Subject = 'New task';
            finalList.add(newTask);
        }
        insert finalList;
    }

    public static void oppClosedTask(List<Opportunity> oppList){

        List<Task> finalList = new List<Task>();

        for (Opportunity iterator: oppList){
            if (iterator.StageName == 'Closed Won' || iterator.StageName == 'Closed Lost'){
                //Do nothing. Optionally, use != operator
            }
            else{
                Task newTask = new Task();
                newTask.WhatId = iterator.id;
                newTask.Subject = iterator.StageName;
                finalList.add(newTask);
            }
        }
        insert finalList;
    }

    public static void oppChangeTask(Map<ID, Opportunity> oldList, List<Opportunity> newList){


        for(Opportunity iterator: newList){

            Opportunity oldOpp = oldList.get(iterator.id);

            Boolean oldValue = oldOpp.stageName.equals('Needs Analysis');
            Boolean newValue = iterator.StageName.equals('Closed Lost');

            if(oldValue && newValue){
                Task newTask = new Task();
                newTask.WhatId = iterator.id;
                newTask.Subject = 'Closed Lost';
                insert newTask;
            }
        }
    }

}
```
