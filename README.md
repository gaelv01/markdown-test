<!--- HEADINGS --->

# This is a h1
## This is a h2
### This is a h3
#### This is a h4
##### This is a h5
###### This is a h6


<!-- TEXT STYLES -->

*This is an italic text.*

**This is a strong text**

~~This is a striked text.~~

<!-- UNORDERED LISTS -->

* Apple
    * Red apple
    * Green apple
* Orange
* Banana
* Etc

<!-- ORDERED LISTS -->

1. Apple
    1. Red apple
    2. Green apple
2. Orange
3. Banana
4. Etc.

<!-- LINKS -->

[google.com](https://www.google.com)

[google.com](https://www.google.com "Custom title")

<!-- QUOTES -->

> This is a quote.

<!-- HORIZONTAL DIVIDERS -->

---
___

<!-- CODE VERBOSE -->

`console.log('Hello Markdown!')`

```javascript
const express = require("express");
const user = express.Router();
const db = require("../config/database");
const jwt = require("jsonwebtoken");

user.post("/login", async (req, res, next) => {
  const { user_mail, user_password } = req.body;
  const query = `SELECT * FROM user WHERE user_mail = '${user_mail}' AND user_password = '${user_password}';`;
  const rows = await db.query(query);

  if (user_mail && user_password) {
    if (rows.length == 1) {
      const token = jwt.sign(
        {
          user_id: rows[0].user_id,
          user_mail: rows[0].user_mail,
        },
        "debugkey",
        { expiresIn: "1h" }
      );
      return res.status(200).json({ code: 200, message: token });
    } else {
      return res
        .status(200)
        .json({ code: 401, message: "User or password are incorrect." });
    }
  } else {
    return res.status(200).json({ code: 500, message: "Missing fields." });
  }
});

module.exports = user;
```

```python
print('Hello Markdown!')
```
```html
<h1>Hello Markdown!</h1>
```

<!-- Tables -->

| Tables | Are | Cool |
| ------- |:-------:| ------: |
|test|test|test|

<!-- IMAGES -->

<!-- ![VSCODIUM LOGO](https://upload.wikimedia.org/wikipedia/commons/5/56/VSCodium_Logo.png) -->

![VSCodium Logo](/images/VSCodium_Logo.png "VSCodium Logo")

<!-- GITHUB MARKDOWN -->

<!-- TO DO LISTS -->

* [x] Task 1
* [x] Task 2
* [x] Task 3
* [] Task 4
