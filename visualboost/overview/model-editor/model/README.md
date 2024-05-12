# Model

## Overview:

In the context of VisualBoost, a model defines a technical object.&#x20;

To specify a model, properties can be created. These characterize the entity. For example, for an address data model, properties such as email, name, and birthdate can be defined.&#x20;



<figure><img src="../../../.gitbook/assets/2024-05-11 14_38_02-Window.png" alt="" width="220"><figcaption></figcaption></figure>

The **email** property is indicated by an exclamation mark (**!**), signifying that it is required.

VisualBoost offers the possibility to further customize these properties, such as specifying whether an attribute is required or should be unique. Overall, a model helps to clearly define and organize how a backend application is structured and stores data, making it easier to develop and manage the application.



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

