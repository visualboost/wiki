# Configuration

In the configuration section, you can further customize the backend application (currently only NodeJS).&#x20;

{% hint style="info" %}
The settings are used to generate environment variables that the application uses for its configuration.
{% endhint %}

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

This includes:

* **Structure**: The project and folder structure
* **Server**: server parameters such as port number and API key
* **Database**: database parameters like username, password, and port.&#x20;



## Structure

***

All the following directories are relative to the directory that contains the backend application:

The generated backend is located in `/home/vb/myfirstapp/backend` and the **database directory** is `/db/generated`.  That means that the absolute path of the database directory is `/home/vb/myfirstapp/backend/db/generated`.

### Directories

* Database Directory: This directory contains all database models and subdocuments (MongoDB).
* Routes Directory: This directory contains all rest api routes.&#x20;
* Extension route directory: This directory can be used to create custom routes. To create a custom route
* Test directory

## Access Environment Variables
