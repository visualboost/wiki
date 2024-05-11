# Model

## Overview:

In the context of VisualBoost, a model defines a technical object.&#x20;

To specify a model, properties can be created. These characterize the entity. For example, for an address data model, properties such as email, name, and birthdate can be defined.&#x20;

<figure><img src="../../../.gitbook/assets/2024-05-11 13_28_25-Window.png" alt=""><figcaption></figcaption></figure>

The **email** property is indicated by an exclamation mark (**!**), signifying that it is required.

VisualBoost offers the possibility to further customize these properties, such as specifying whether an attribute is required or should be unique. Overall, a model helps to clearly define and organize how a backend application is structured and stores data, making it easier to develop and manage the application.



## Model in NodeJS:

When generating the backend application, a model is translated into two distinct files. One file contains the database structure of the model, while the other file includes the routes for the REST API.



{% tabs %}
{% tab title="./db/Person.js" %}
{% code overflow="wrap" lineNumbers="true" fullWidth="true" %}
```javascript
mongoose = require("mongoose");
const Schema = mongoose.Schema;

const PersonSchema = new Schema(
    {
        email: {
            type: String,
            required: true,
            indexed: false,
            unique: false,
        },
        name: { 
            type: String, 
            required: false, 
            indexed: false, 
            unique: false},
        birthdate: {
            type: Date,
            required: false,
            indexed: false,
            unique: false,
        }
    },
    {timestamps: true},
);

module.exports = mongoose.model("Person", PersonSchema, "Person");
```
{% endcode %}


{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}
