# Configuration

In the configuration section, you can further customize the backend application (currently only NodeJS).&#x20;

{% hint style="info" %}
The settings are used to generate environment variables that the application uses for its configuration. The environment variables are not pushed to the Git repository for security reasons. They must be created manually during the initial setup and updated whenever there are changes.
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

* **Database Directory:** This directory contains all database models and subdocuments (MongoDB).
* **Routes Directory:** This directory contains all [rest api routes](../../model-editor/model/functions/).&#x20;
* **Extension route directory:** Contains all [custom functions](../../model-editor/model/functions/).
* **Test directory:** Contains all **\*.http files**.



## Server

* **NodeJS version**: The NodeJS version that is used for the server application.
* **Port**: The port of the server application.
* **API-Key**: The API-Key that is used to access the routes. The API-Key can be changed by clicking the refresh button. **Note**: If the API-Key is updated, it must also be updated in the NodeJS project (.env file).

{% hint style="info" %}
**Note:** The API-Key is included in the request header as **'x-api-key'**.
{% endhint %}

## Access Environment Variables
