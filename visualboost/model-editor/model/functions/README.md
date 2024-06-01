---
description: >-
  For each model, functions can be created to create, read, update and deleted
  the model (CRUD). If the CRUD functions are not sufficient, custom business
  logic can be added.
---

# Functions

## CRUD

For each model, multiple `READ`, `UPDATE`, and `DELETE` functions can be created, but only one `CREATE` function.

| Function   | Description                                                                                                      |
| ---------- | ---------------------------------------------------------------------------------------------------------------- |
| `CREATE`   | Creates a new database entry of the model and returns it to the client.                                          |
| `READ`     | Finds a single database entry of the model by a path and/or query parameters and returns it to the client.       |
| `READ_ALL` | Finds multiple database entries of the model and returns it to the client. Can be specified by query parameters. |
| `UPDATE`   | Updates an existing database entry and returns it to the client. Can be specified by path and query parameters.  |
| `DELETE`   | Deletes an existing database entry and returns it to the client. Can be specified by path and query parameters.  |

## Path Parameter

Path parameters can be used to adapt and specify single operations. When creating a CRUD function, the path parameter "\_id" is used by default. This parameter can be replaced with another property of a model. A _path parameter_ corresponds to an equals query.The following property types are currently supported:

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
