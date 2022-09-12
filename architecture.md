## Trigger Framework
In our projects, we use [Trigger Framework](https://github.com/kevinohara80/sfdc-trigger-framework) for writing our triggers, because of [several reasons](https://trailhead.salesforce.com/content/learn/modules/success-cloud-coding-conventions/implement-frameworks-sc).
This trigger framework bundles a single `TriggerHandler` base class that you can inherit from in all of your trigger handlers. The base class includes context-specific methods that are automatically called when a trigger is executed.

To create a trigger handler, you simply need to create a class that inherits from TriggerHandler.cls. Here is an example for creating an Opportunity trigger handler.

```Apex
public class OpportunityTriggerHandler extends TriggerHandler {
```
In your trigger handler, to add logic to any of the trigger contexts, you only need to override them in your trigger handler. Here is how we would add logic to a beforeUpdate trigger.

```Apex
public class OpportunityTriggerHandler extends TriggerHandler {
  private List<Opportunity> newOpportunityList;
  private List<Opportunity> oldOpportunityList;
  private Map<Id, Opportunity> newOpportunityMap;
  private Map<Id, Opportunity> oldOpportunityMap;

  public OpportunityTriggerHandler() {
      this.newOpportunityList = (List<Opportunity>) Trigger.new;
      this.oldOpportunityList = (List<Opportunity>) Trigger.old;
      this.newOpportunityMap = (Map<Id, Opportunity>) Trigger.newMap;
      this.oldOpportunityMap = (Map<Id, Opportunity>) Trigger.oldMap;
  }
    
  public override void beforeUpdate() {
    OpportunityService.callMethod(oldOpportunityMap, newOpportunityMap);
  }
}
```
To use the trigger handler, you only need to construct an instance of your trigger handler within the trigger handler itself and call the run() method. Here is an example of the Opportunity trigger.

```Apex
trigger OpportunityTrigger on Opportunity (before insert, before update) {
  new OpportunityTriggerHandler().run();
}
```
## Important info!
Create only **one** trigger, **one** triggerhandler and **one** service classes per one object. If there is already created classes for object, which you want to implement trigger - you should just extend the existing classes.
