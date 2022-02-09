writeCode

var express = require('express')
var mongoose = require('mongoose')
var Product = require('./models/product')

mongoose.connect()

var app = express('mongodb://localhost/sample', {
useNewUrlParser: true, useUnifiedTopology: true
}, (err) => {
    console.log(err ? err : 'connected')
})

app.get('/', (req,res) => {
    res.send('welcome')
})
app.post('/products', (req,res) => {
    console.log(req.body)
    //save data to db
    Product.create(req.body, (err, product) => {
        console.log(err, product)
    })
})

app.get('/products', (req,res) => {
    Product.find({},(err, products) =>{
        console.log(err,products)
        //res.json({products: products})
    })
})

app.put('/products/:id', (req,res)=>{
    var id = req.params.id
    Product.findByIdAndUpdate(iq, req.body, {new:true}, (err, updatedProduct) => {
        res.json(updatedProduct)
    })
})

app.delete('/products/:id', (req,res) => {
    Product.findByIdAndUpdate(req.params.id, (err,deletedProduct) => {
       // res.json()
        res.send(`${deletedProduct.title} was deleted`)

    })
})


var userSchema = new Schema({
  name: String,
  email: String,
  sports: String
})

#### Perform users CRUD operation using mongoose from an express application

- create an express application named sample
- connect to mongodb database using mongoose.connect() in `app.js`
- create a user schema in models directory
  - name
  - email
  - sports
- create user model based on schema
- export it from model
- import it into app.js
- on POST request on `/users` route create a user

Q. Insert a user into database using Model.create() OR model.save() function

- insert user `{name: '', email: '', sports: ['cricket', 'khokho']}`
- check into your local mongo database for inserted data

Q. Query all the users from the database

- use Model.find

Q. query a single document(user) using mongoose

- on GET request on '/users/:id' route, fetch a user
- use Model.find({\_id: 'some-id'}) // use \_id of inserted document in database
- use Model.findOne({\_id: 'some-id'})
- use Model.findById(id)

Mention the difference between them in comments, if any ?

Q. Update a user

- on PUT request on '/users/:id', update a user
- use Model.update
- use Model.updateOne
- use Model.findByIdAndUpdate(id)

Q. delete a user using Model.findByIdAndDelete()

- on DELETE request on '/users/:id'

For example:-

```js
// import User model at top
const User = require("./models/user");

// delete route for deleting a user using id
app.delete("/users", (req, res) => {
  var userId = "some id from database";
  User.findByIdAndDelete(id, (err, user) => {
    if (err) return next(err);
    res.send("user deleted");
  });
});
```

Similarily, handle all above routes taking help from delete route.
