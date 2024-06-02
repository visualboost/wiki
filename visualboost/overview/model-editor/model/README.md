# Models & Classes

## Overview:

In the context of VisualBoost, a **Model** defines a technical object than can be specified by property and functions (CRUD and custom functions). **Classes**, on the other hand, represent simple data objects which can only be extended with their own business logic but not with CRUD functions.&#x20;

{% hint style="info" %}
At the database level (MongoDB), a separate collection is created for each model. Classes, on the other hand, correspond to subdocuments.
{% endhint %}



To specify a model, properties can be created. These characterize the entity. For example, for an address data model, properties such as email, name, and birthdate can be defined.&#x20;



<figure><img src="../../../.gitbook/assets/2024-05-11 14_38_02-Window.png" alt="" width="220"><figcaption></figcaption></figure>

The **email** property is indicated by an exclamation mark (**!**), signifying that it is required.

VisualBoost offers the possibility to further customize these properties, such as specifying whether an attribute is required or should be unique. Overall, a model helps to clearly define and organize how a backend application is structured and stores data, making it easier to develop and manage the application.

In the next sections, we'll explain how we use the defined models to generate source code.

## Model in NodeJS (Backend):

When generating the backend application, a model is translated into two distinct files. One file contains the database structure of the model, while the other file includes the routes for the REST API.

{% tabs %}
{% tab title="./db/generated/AddressData.js" %}
{% code overflow="wrap" lineNumbers="true" fullWidth="true" %}
```javascript
const mongoose = require("mongoose");
const Schema = mongoose.Schema;
const ObjectId = mongoose.Types.ObjectId;

const AddressDataSchema = new Schema(
    {
        email: { type: String, required: true, indexed: false, unique: false },
        name: { type: String, required: false, indexed: false, unique: false },
        birthdate: {
            type: Date,
            required: false,
            indexed: false,
            unique: false,
        },
    },
    { timestamps: true },
);

module.exports = mongoose.model(
    "AddressData",
    AddressDataSchema,
    "AddressData",
);
```
{% endcode %}
{% endtab %}

{% tab title="./routes/generated/AddressData.js" %}
{% code overflow="wrap" lineNumbers="true" %}
```javascript
const router = require("express").Router();
const mongoose = require("mongoose");
const AddressData = require("./../../db/generated/AddressData");

/**
 * Get a AddressData by _id
 **/
router.get("/addressdata/:_id", async (req, res, next) => {
    try {
        if (!req.params._id) {
            return res
                .status(400)
                .json({
                    error: "Parameter '_id' is required but not provided.",
                });
        }

        const addressdata = await AddressData.findOne(
            { _id: req.params._id },
            "-__v",
            { minimize: true },
        );

        if (!addressdata) {
            return res.status(404).send("Not Found");
        }

        return res.json(addressdata);
    } catch (e) {
        console.error(e);
        return res.status(500).send("Internal Server Error");
    }
});

/**
 * Get all AddressData
 **/
router.get("/addressdatas", async (req, res, next) => {
    try {
        const addressdata = await AddressData.find({}, "-__v", {
            minimize: true,
        });

        return res.json(addressdata);
    } catch (e) {
        console.error(e);
        return res.status(500).send("Internal Server Error");
    }
});

/**
 * Creates a new AddressData
 **/
router.post("/addressdata", async (req, res, next) => {
    try {
        const input = req.body;

        if (input.email === undefined || input.email === null) {
            return res
                .status(400)
                .json({ error: "email is required but not provided." });
        }

        let addressdata = await AddressData.create({ ...input });
        addressdata = await AddressData.findOne({ _id: addressdata._id });

        return res.json(addressdata);
    } catch (e) {
        console.error(e);
        return res.status(500).send("Internal Server Error");
    }
});

/**
 * Update an existing AddressData
 **/
router.put("/addressdata/:_id", async (req, res, next) => {
    try {
        if (!req.params._id) {
            return res
                .status(400)
                .json({
                    error: "Parameter '_id' is required but not provided.",
                });
        }

        const id = req.params._id;
        const input = req.body;

        if (input.email === undefined || input.email === null) {
            return res
                .status(400)
                .json({ error: "email is required but not provided." });
        }

        const addressdata = await AddressData.findOneAndUpdate(
            { _id: req.params._id },
            { ...input },
            { new: true, lean: true },
        );

        if (!addressdata) {
            return res.status(404).send("Not Found");
        }

        return res.json(addressdata);
    } catch (e) {
        console.error(e);
        return res.status(500).send("Internal Server Error");
    }
});

/**
 * Delete an existing AddressData
 **/
router.delete("/addressdata/:_id", async (req, res, next) => {
    try {
        if (!req.params._id) {
            return res
                .status(400)
                .json({
                    error: "Parameter '_id' is required but not provided.",
                });
        }

        const id = req.params._id;
        const addressdata = await AddressData.findOneAndDelete(
            { _id: req.params._id },
            { __v: 0 },
        );

        if (!addressdata) {
            return res.status(404).send("Not Found");
        }

        return res.json(addressdata);
    } catch (e) {
        console.error(e);
        return res.status(500).send("Internal Server Error");
    }
});

module.exports = router;
```
{% endcode %}
{% endtab %}
{% endtabs %}



## Model in Java (Client):

When generating the client code, a model is translated into multiple files.&#x20;

* **Data** Class: The Model as Java class.
* **DTO** Class: Represents the request body for **CREATE** and **UPDATE** functions.
* **API** Class: Contains all functions.

{% tabs %}
{% tab title="AddressData.java" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
package api.model;

import java.util.Date;

public class AddressData {

  private String _id;
  private String email;
  private String name;
  private Date birthdate;

  public AddressData(String _id, String email, String name, Date birthdate) {
    this._id = _id;
    this.email = email;
    this.name = name;
    this.birthdate = birthdate;
  }

  public String getId() {
    return this._id;
  }

  public void setId(String _id) {
    this._id = _id;
  }

  public String getEmail() {
    return this.email;
  }

  public void setEmail(String email) {
    this.email = email;
  }

  public String getName() {
    return this.name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public Date getBirthdate() {
    return this.birthdate;
  }

  public void setBirthdate(Date birthdate) {
    this.birthdate = birthdate;
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="CreateAddressDataRequestBody .java" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
package api.model.dto;

import java.util.Date;

public class CreateAddressDataRequestBody {

  private String email;
  private String name;
  private Date birthdate;

  public CreateAddressDataRequestBody(
    String email,
    String name,
    Date birthdate
  ) {
    this.email = email;
    this.name = name;
    this.birthdate = birthdate;
  }

  public String getEmail() {
    return this.email;
  }

  public void setEmail(String email) {
    this.email = email;
  }

  public String getName() {
    return this.name;
  }

  public void setName(String name) {
    this.name = name;
  }

  public Date getBirthdate() {
    return this.birthdate;
  }

  public void setBirthdate(Date birthdate) {
    this.birthdate = birthdate;
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="API.java" %}
{% code overflow="wrap" lineNumbers="true" %}
```java
package api;

import api.model.AddressData;
import api.model.dto.CreateAddressDataRequestBody;
import api.model.dto.UpdateAddressDataRequestBody;
import com.google.gson.Gson;
import com.google.gson.reflect.TypeToken;
import java.io.IOException;
import java.lang.reflect.Type;
import java.util.ArrayList;
import okhttp3.*;

public class API {

  public static final String version = "0.0.31";

  private static API instance;

  private String apiKey;

  private String domain;

  private int port = 0;

  private OkHttpClient httpClient;

  private API() {
    this.httpClient = new OkHttpClient();
  }

  public static API getInstance() {
    if (instance == null) {
      instance = new API();
    }

    return instance;
  }

  public API domain(String domain) {
    this.domain = domain;
    return getInstance();
  }

  public API apiKey(String apiKey) {
    this.apiKey = apiKey;
    return getInstance();
  }

  public String getApiKey() {
    return apiKey;
  }

  public API port(int port) {
    this.port = port;
    return getInstance();
  }

  public String getDomain() {
    return domain;
  }

  public int getPort() {
    return port;
  }

  public String getUrl() {
    String domain = this.domain;
    if (this.port > 0) {
      domain += ":" + port;
    }

    return domain;
  }

  public OkHttpClient getHttpClient() {
    return httpClient;
  }

  public void setHttpClient(OkHttpClient httpClient) {
    this.httpClient = httpClient;
  }

  /**
   * Creates a new AddressData
   **/
  public AddressData createAddressData(CreateAddressDataRequestBody body)
    throws Exception {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .post(
        RequestBody.create(
          gson.toJson(body),
          MediaType.parse("application/json")
        )
      )
      .build();

    Response httpResponse = this.httpClient.newCall(request).execute();

    int statusCode = httpResponse.code();
    String response = httpResponse.body().string();

    if (statusCode < 200 || statusCode >= 300) {
      throw new HttpException(statusCode, response);
    }

    return gson.fromJson(response, AddressData.class);
  }

  /**
   * Delete an existing AddressData
   **/
  public AddressData deleteAddressData(String _id) throws Exception {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + _id + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .delete()
      .build();

    Response httpResponse = this.httpClient.newCall(request).execute();

    int statusCode = httpResponse.code();
    String response = httpResponse.body().string();

    if (statusCode < 200 || statusCode >= 300) {
      throw new HttpException(statusCode, response);
    }

    return gson.fromJson(response, AddressData.class);
  }

  /**
   * Get a AddressData by _id
   **/
  public AddressData getAddressData(String _id) throws Exception {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + _id + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .get()
      .build();

    Response httpResponse = this.httpClient.newCall(request).execute();

    int statusCode = httpResponse.code();
    String response = httpResponse.body().string();

    if (statusCode < 200 || statusCode >= 300) {
      throw new HttpException(statusCode, response);
    }

    return gson.fromJson(response, AddressData.class);
  }

  /**
   * Get all AddressData
   **/
  public ArrayList<AddressData> getAllAddressData() throws Exception {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdatas/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .get()
      .build();

    Response httpResponse = this.httpClient.newCall(request).execute();

    int statusCode = httpResponse.code();
    String response = httpResponse.body().string();

    if (statusCode < 200 || statusCode >= 300) {
      throw new HttpException(statusCode, response);
    }

    Type type = new TypeToken<ArrayList<AddressData>>() {}.getType();
    return gson.fromJson(response, type);
  }

  /**
   * Update an existing AddressData
   **/
  public AddressData updateAddressData(UpdateAddressDataRequestBody body)
    throws Exception {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + body.getId() + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .put(
        RequestBody.create(
          gson.toJson(body),
          MediaType.parse("application/json")
        )
      )
      .build();

    Response httpResponse = this.httpClient.newCall(request).execute();

    int statusCode = httpResponse.code();
    String response = httpResponse.body().string();

    if (statusCode < 200 || statusCode >= 300) {
      throw new HttpException(statusCode, response);
    }

    return gson.fromJson(response, AddressData.class);
  }

  /**
   * Creates a new AddressData
   **/
  public void createAddressData(
    CreateAddressDataRequestBody body,
    AsyncCallback<AddressData> callback
  ) {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .post(
        RequestBody.create(
          gson.toJson(body),
          MediaType.parse("application/json")
        )
      )
      .build();

    this.httpClient.newCall(request)
      .enqueue(
        new Callback() {
          @Override
          public void onFailure(Call call, IOException e) {
            callback.onError(e);
          }

          @Override
          public void onResponse(Call call, Response httpResponse)
            throws IOException {
            int statusCode = httpResponse.code();
            String response = httpResponse.body().string();

            if (statusCode < 200 || statusCode >= 300) {
              callback.onError(new HttpException(statusCode, response));
            }

            callback.onSuccess(gson.fromJson(response, AddressData.class));
          }
        }
      );
  }

  /**
   * Delete an existing AddressData
   **/
  public void deleteAddressData(
    String _id,
    AsyncCallback<AddressData> callback
  ) {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + _id + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .delete()
      .build();

    this.httpClient.newCall(request)
      .enqueue(
        new Callback() {
          @Override
          public void onFailure(Call call, IOException e) {
            callback.onError(e);
          }

          @Override
          public void onResponse(Call call, Response httpResponse)
            throws IOException {
            int statusCode = httpResponse.code();
            String response = httpResponse.body().string();

            if (statusCode < 200 || statusCode >= 300) {
              callback.onError(new HttpException(statusCode, response));
            }

            callback.onSuccess(gson.fromJson(response, AddressData.class));
          }
        }
      );
  }

  /**
   * Get a AddressData by _id
   **/
  public void getAddressData(String _id, AsyncCallback<AddressData> callback) {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + _id + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .get()
      .build();

    this.httpClient.newCall(request)
      .enqueue(
        new Callback() {
          @Override
          public void onFailure(Call call, IOException e) {
            callback.onError(e);
          }

          @Override
          public void onResponse(Call call, Response httpResponse)
            throws IOException {
            int statusCode = httpResponse.code();
            String response = httpResponse.body().string();

            if (statusCode < 200 || statusCode >= 300) {
              callback.onError(new HttpException(statusCode, response));
            }

            callback.onSuccess(gson.fromJson(response, AddressData.class));
          }
        }
      );
  }

  /**
   * Get all AddressData
   **/
  public void getAllAddressData(
    AsyncCallback<ArrayList<AddressData>> callback
  ) {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdatas/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .get()
      .build();

    this.httpClient.newCall(request)
      .enqueue(
        new Callback() {
          @Override
          public void onFailure(Call call, IOException e) {
            callback.onError(e);
          }

          @Override
          public void onResponse(Call call, Response httpResponse)
            throws IOException {
            int statusCode = httpResponse.code();
            String response = httpResponse.body().string();

            if (statusCode < 200 || statusCode >= 300) {
              callback.onError(new HttpException(statusCode, response));
            }

            Type type = new TypeToken<ArrayList<AddressData>>() {}.getType();
            callback.onSuccess(gson.fromJson(response, type));
          }
        }
      );
  }

  /**
   * Update an existing AddressData
   **/
  public void updateAddressData(
    UpdateAddressDataRequestBody body,
    AsyncCallback<AddressData> callback
  ) {
    Gson gson = JsonSerializer.getInstance().getGson();

    Request request = new Request.Builder()
      .url(getUrl() + "/addressdata/" + body.getId() + "/")
      .header("Content-Type", "application/json")
      .header("x-api-key", apiKey)
      .put(
        RequestBody.create(
          gson.toJson(body),
          MediaType.parse("application/json")
        )
      )
      .build();

    this.httpClient.newCall(request)
      .enqueue(
        new Callback() {
          @Override
          public void onFailure(Call call, IOException e) {
            callback.onError(e);
          }

          @Override
          public void onResponse(Call call, Response httpResponse)
            throws IOException {
            int statusCode = httpResponse.code();
            String response = httpResponse.body().string();

            if (statusCode < 200 || statusCode >= 300) {
              callback.onError(new HttpException(statusCode, response));
            }

            callback.onSuccess(gson.fromJson(response, AddressData.class));
          }
        }
      );
  }

  public interface AsyncCallback<T> {
    public void onSuccess(T response);

    public void onError(Exception error);
  }
}
```
{% endcode %}
{% endtab %}
{% endtabs %}
