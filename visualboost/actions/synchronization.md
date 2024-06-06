# Synchronization

```javascript
const router = require("express").Router();

/**
 * This is an example of a custom function
 *
 * @name: myCustomFunction
 *
 * @body: {
 *    name: string
 * }
 *
 * @return: ./../../db/generated/MyModel
 *
 * @errors: {
 *     400: "Bad Request",
 *     404: "Not found",
 *     500: "Internal Server Error"
 * }
 **/
router.post("/custom/route/:some_path_param", async (req, res, next) => {

    /**
     * Add some business logic here...
     */

});

module.exports = router;
```
