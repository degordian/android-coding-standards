# Tips & tricks

## 1. In DBFlow, for nested OneToMany or ManyToMany relations, the save(), delete() etc. methods will not be called
##    on the list of related objects. Disable efficientMethods for those methods to be called.


### If there's an Ant object with it's own OneToMany or ManyToMany relation, two outcomes are possible.

### a) Nested relation objects of an Ant will NOT be saved when called Queen.save():

```java
   public class Queen extends BaseModel {

      @OneToMany(methods = {OneToMany.Method.ALL}, variableName = "ants", <b>efficientMethods = true</b>)
      public List<Ant> getMyAnts() { ... }
```

### b) Nested relation objects of an Ant object will be saved when called Queen.save():

```java
   public class Queen extends BaseModel {

      @OneToMany(methods = {OneToMany.Method.ALL}, variableName = "ants", <b>efficientMethods = false</b>)
      public List<Ant> getMyAnts() { ... }
```
