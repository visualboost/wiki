# Quick-Start

{% hint style="info" %}
Alternatively, you can also watch our [video tutorial](https://www.youtube.com/watch?v=DO3IQ9kLYxw\&list=PL\_KLQBBjBxQaxzPsSb6UckLbwmTkG27Fm\&index=2).
{% endhint %}

In this chapter, you will learn how to create a model, a class, an enum, and a package. Each section will guide you through the process of building these components step-by-step.

Before getting started, navigate to the Model Editor. It should look like this:

<figure><img src="../.gitbook/assets/Modeleditor2.png" alt=""><figcaption></figcaption></figure>

## Create a Model:

To create a model, right-click on the white surface and navigate to **Add** -> **New Model**.

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

Now, specify the name of your model and confirm by clicking **Create**.

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Congratulations, you have created your first model. The result should now look like this:

<figure><img src="../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>



### Specify your Model:

{% hint style="info" %}
Every model and class has a parameter called **\_id**. This parameter is used to uniquely identify each entry in the database.
{% endhint %}

To specify a model, double-click on the model. A dialog will appear where you can add additional properties and functions.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

To add a new property, click on the plus symbol.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Then, enter the name and data type of your new property. Confirm by clicking on **Add**.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

The property has been added to the model. Similarly, you can further specify your model. For more information about properties, refer to the [details provided here.](model/properties.md)

## Create a Class:

Creating a class is similar to creating a model. Navigate to **Add** -> **New Class**.

<figure><img src="../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>



Now enter your class name and confirm by clicking **Create:**

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

## Create a Connection:

Currently, there is no relationship between your model and your class.&#x20;

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

To establish a connection between them, click on the connection point of your model. Then, hold down the left mouse button and drag the connection to a connection point of your class:

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Step 1: Click the connection point</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Step 2: Drag the connection to a connection point of the class</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>Result: The Model is connect with the class</p></figcaption></figure>

## Create an Enum:

Creating an enum follows the same process as creating a class. Navigate to **Add** -> **New Enum** and specify the name of your enum.

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Doubleclick your enum to specify it. In the input field labeled **Values**, enter your values and confirm with Enter. Once you're done, click on **Save**.

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

You can establish a connection between a model or class and an enum similar to the [Create a connection chapter](quick-start.md#create-a-connection).

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>



## Create a Package:

Create a package by clicking on **Add** -> **New Package.** Enter a package name and config by clicking **Create**.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Resize your package by clicking and holding the resize icon, then moving your mouse.

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

Now add your Model, Class and Enum to the newly created package by dragging them into the package.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>



