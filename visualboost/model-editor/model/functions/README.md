---
description: >-
  For each model, functions can be created to create, read, update and deleted
  the model (CRUD). If the CRUD functions are not sufficient, custom business
  logic can be added.
---

# Functions

## CRUD

***

For each model, multiple `READ`, `UPDATE`, and `DELETE` functions can be created, but only one `CREATE` function.

<table><thead><tr><th width="150">Function</th><th width="180">HTTP-Method</th><th>Description</th></tr></thead><tbody><tr><td><code>CREATE</code></td><td><code>POST</code></td><td>Creates a new database entry of the model and returns it to the client.</td></tr><tr><td><code>READ</code></td><td><code>GET</code></td><td>Finds a single database entry of the model by a path and/or query parameters and returns it to the client.</td></tr><tr><td><code>READ_ALL</code></td><td><code>GET</code></td><td>Finds multiple database entries of the model and returns it to the client. Can be specified by query parameters.</td></tr><tr><td><code>UPDATE</code></td><td><code>PUT</code></td><td>Updates an existing database entry and returns it to the client. Can be specified by path and query parameters.</td></tr><tr><td><code>DELETE</code></td><td><code>DELETE</code></td><td>Deletes an existing database entry and returns it to the client. Can be specified by path and query parameters.</td></tr></tbody></table>



### Path Parameter

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



### Query Parameter

Query parameters are used as search criteria or filtering options. They allow users to dynamically modify the content they receive by including key-value pairs, like `?name="Stephen"&age=24`, in the URL. At the moment, VisualBoost provides the nine different query operations, that can be specified in the `Path` input field of your CRUD function.

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

#### Operators:

<table><thead><tr><th width="190">Query</th><th width="115" align="center">Operator</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td><code>EQUAL</code></td><td align="center">=</td><td>/persons?name=</td><td></td></tr><tr><td><code>NOT_EQUAL</code></td><td align="center">!=</td><td>/persons?name!=</td><td></td></tr><tr><td><code>LOWER</code></td><td align="center">&#x3C;</td><td>/persons?age&#x3C;</td><td></td></tr><tr><td><code>LOWER_THAN</code></td><td align="center">&#x3C;=</td><td>/persons?age&#x3C;=</td><td></td></tr><tr><td><code>GREATER</code></td><td align="center">></td><td>/persons?name></td><td></td></tr><tr><td><code>GREATER_THAN</code></td><td align="center">>=</td><td>/persons?age>=</td><td></td></tr><tr><td><code>IN</code></td><td align="center">.in()</td><td>/persons?age.in()</td><td></td></tr><tr><td><code>REGEX</code></td><td align="center">.regex()</td><td>/persons?name.regex()</td><td>Only for text properties</td></tr><tr><td><code>NEAR</code></td><td align="center">.near()</td><td>/persons?location.near()</td><td>Only for location properties</td></tr></tbody></table>

Static Values

<mark style="color:purple;">Still in progress....</mark>



## Extensions (Custom Functions)

<mark style="color:purple;">Still in progress....</mark>
