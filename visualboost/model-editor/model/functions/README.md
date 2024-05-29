# Functions

## Path Parameter

When creating a CRUD function, the path parameter "\_id" is used by default. This parameter can be replaced with another property of a model. A _path parameter_ corresponds to an equals query.The following property types are currently supported:

| Type        | Example                 | Description                                                                                                                                                             |
| ----------- | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Boolean     | /persons/_hasJob_       | Return all peoplewith a job. The Model `Person`contains a boolean property called `hasJob`.                                                                             |
| Text        | /persons/_name_         | Return all people with the same name. The Model `Person` contains a text property called `name`.                                                                        |
| Enumeration | /persons/_gender_       | Return all people with the same gender. The Model `Person` contains a reference to an Enum called `gender`.                                                             |
| Integer     | /persons/_age_          | Return all people within the same age. The Model `Person` contains an int property called `age`.                                                                        |
| Float       | /persons/_money_        | Return all people within the same bank balance. The Model `Person` contains a float property called `money`.                                                            |
| Date        | /persons/_birthdate_    | Return all people within the same birthdate. The Model `Person` contains a date property called `birthdate`.                                                            |
| File        | /person/profil\_picture | Return a person with a certain profile picture. The Model `Person` contains a file property called `profil_picture`. The file `_id` needs to be used as the value here. |



During the execution of the REST call, a value must be provided instead of the property:

**Example:**

```
# Give me all the people who are 24 years old.
/persons/24
```

{% hint style="info" %}
Location is currently not supported.
{% endhint %}

{% hint style="info" %}
At the current time, only one path parameter is allowed
{% endhint %}
