writeCode

Create a simple express app(app.js)

- connect to local mongodb database using `mongoose.connect`
- add article schema(article.js) using mongoose inside models directory.

var express = require('express')
var mongoose = require('mongoose')
var Schema = mongoose.Schema

app.use(express.json())
app.use(express.urlencoded({extended:false}))

mongoose.connect('mongodb://localhost/sample', {
  userNewUrlParser: true, useUnifiedTopology: true
  }, (err) => {
    console.log(err? err: 'connected')
  }
})


var app = express()

app.get('/', (req, res) => {
  res.send('<h2>Welcome</h2>)
})

app.listen(3000, () => {})
