# tenkipay-php
Nodejs ExpressJS tenkipay webhook integration

# Instructions
Create a expressjs file
<code> touch tenkipay.js</code>

Exclude your webhook URL for sending CRS token and CORS, for Tenkipay to post

configure your webhook url on tenkipay
add your webhook secret to .env
TENKIPAY_SECRET="{your webhook secret}"
Open  tenkipay.js and add the post route.

```
//transaction payload
const express = require('express')
const bodyParser = require('body-parser')
const app = express();
app.use(bodyparser.urlencoded({ extended: true }))
app.use(bodyparser.json())

app.post('/webhook',(req, res)=> {
    let tenki_key = TENKIPAY_SECRET
    let secret = req.body.secret
    if(secret !== tenki_key || secret===undefined){
       res.status(403).end()
       return;
    }
    req.body.description
    req.body.customeremail
    req.body.customer_username
    req.body.amount
    res.status(200).end();
})
 ```
