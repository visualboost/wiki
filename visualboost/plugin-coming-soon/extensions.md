# Extensions

VisualBoost makes it easy to customize your application and add your own business logic by allowing you to create [Extensions](../model-editor/model/functions/extension.md). These Extensions are custom REST routes that can run their own unique functionality and are linked to specific models. For each model, you can add as many REST routes as you need. You can also synchronize these Extensions with VisualBoost, ensuring they fully integrate into your software architecture. Once synchronized, your Extensions will automatically be included in the documentation.&#x20;

Each Extension is part of a JavaScript file named after the corresponding model. To ensure it is recognized during synchronization, this file must be placed in the Extensions folder, which can be set in VisualBoost’s settings.&#x20;

The plugin automates these steps, making it easy to add an Extension. Simply right-click on the root folder, select **File -> Extension** and choose the model for which you want to create the Extension.

<figure><img src="../.gitbook/assets/add_extension.gif" alt=""><figcaption><p>Creating a new extension</p></figcaption></figure>

To add a new extension you can use one of the following [Live Templates](https://www.jetbrains.com/help/webstorm/using-live-templates.html#live\_templates\_types):&#x20;

{% tabs %}
{% tab title="get" %}
<figure><img src="../.gitbook/assets/add_extension_get.gif" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="post" %}
<figure><img src="../.gitbook/assets/add_extension_post.gif" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="put" %}
<figure><img src="../.gitbook/assets/add_extension_put.gif" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="delete" %}
<figure><img src="../.gitbook/assets/add_extension_delete.gif" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}
