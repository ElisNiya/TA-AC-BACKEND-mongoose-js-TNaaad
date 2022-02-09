writeCode
var express = require('express')
var mongoose = require('mongoose')
var Product = require('./models/product')

var articleSchema = new Schema ({
    title : String,
    description : String,
    tags : String,
    likes : String,
    author : Schema.Types.ObjectId,
    comments : [String]
    }
    {timestamps :true })
    
Design schemas for a blog application which will have

- articles
- comments(on each article) -> may be multiple
- user

Each article can have fields :-

- title
- description
- tags
- likes
- author -> ID of user
- comments
- timestamps()

Each comment can have fields:-

var commentsSchema = new Schema ({
    content: String,
    author : Schema.Types.ObjectId,
    article : String
    }
    {timestamps :true })
    
- content
- author -> ID of user
- article ->
- timestamps()

Each user can have fields:-
var userSchema = new Schema ({
    name: String,
    email : String
    age : String
    })
    
- name
- email
- age

- Design all the schemas and their associated models and export it.
- design in such a way that, they should be associated.

For example:-

- each article and comment should have author
- each comment should belong to one of the article
- add appropriate validations in all schemas



mongoose.export = ('Article', articleSchema)
mongoose.export = ('Users', usersSchema)
mongoose.export = ('Comments', commentsSchema)



