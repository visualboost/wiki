# Java

To enable java code generation for the client side, select **Java** as the programming language under [Configuration > Client](../../../project/settings/configuration/client.md). Additionally, you need to specify three directories where the client code will be generated.

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption><p>Configuration in VisualBoost</p></figcaption></figure>

* **Source directory:** The relative path to a directory that contains the **Root java package.**
* **Root java package:** This directory contains the controller class that can be used to execute the REST functions.
* **Model java package:** This package contains all model, classes and enums.

These settings allow you to configure the folder.

<figure><img src="../../../.gitbook/assets/image (9) (1).png" alt=""><figcaption><p>generated directories and files</p></figcaption></figure>



{% hint style="info" %}
To generate the client side, it is necessary to specify the Git repository for the frontend project in the settings.
{% endhint %}

###

### Dependencies

The generated Java code uses the **OkHttp** library for network communication and **GSON** for the serialization and deserialization of JSON objects.

Therefore, the following dependencies are needed:

{% tabs %}
{% tab title="Maven" %}
```xml
<dependencies>
    <dependency>
        <groupId>com.squareup.okhttp3</groupId>
        <artifactId>okhttp</artifactId>
        <version>4.10.0</version>
    </dependency>

    <dependency>
        <groupId>com.google.code.gson</groupId>
        <artifactId>gson</artifactId>
        <version>2.9.0</version>
    </dependency>
</dependencies>
```
{% endtab %}

{% tab title="Gradle (Kotlin)" %}
```gradle
implementation("com.squareup.okhttp3:okhttp:4.10.0")
implementation("com.google.code.gson:gson:2.9.0")
```
{% endtab %}

{% tab title="Gradle (Groovy)" %}
```gradle
implementation 'com.squareup.okhttp3:okhttp:4.10.0'
implementation 'com.google.code.gson:gson:2.9.0'
```
{% endtab %}
{% endtabs %}

