## OppUpdater

```
trigger oppUpdater on Opportunity (after insert, after update) {

    if(Trigger.isafter){
        if (Trigger.isInsert){
            oppUpdaterHelper.oppInsertTask(trigger.new);
            oppUpdaterHelper.oppClosedTask(trigger.new);
        }

        if (Trigger.isUpdate){
            oppUpdaterHelper.oppChangeTask(trigger.oldMap, trigger.new);
        }
    }
}
```
