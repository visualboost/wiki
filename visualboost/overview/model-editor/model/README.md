# Model

In the context of VisualBoost, a model defines a technical object.&#x20;

To specify a model, properties can be created. These characterize the entity. For example, for an address data model, properties such as email, name, and birthdate can be defined.&#x20;

<figure><img src="../../../.gitbook/assets/2024-05-11 13_28_25-Window.png" alt=""><figcaption></figcaption></figure>

The **email** property is indicated by an exclamation mark (**!**), signifying that it is required.

VisualBoost offers the possibility to further customize these properties, such as specifying whether an attribute is required or should be unique. Overall, a model helps to clearly define and organize how a backend application is structured and stores data, making it easier to develop and manage the application.



In addition, it's important to note that a model always requires a name. This name must be unique within the application scope, meaning it must be unique within a package or globally if the model is not contained within any package.
