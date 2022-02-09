writeCode

Q. Update user schema to

- contains password field with minimum 5 characters and maximim 15
- add createdAt field of type date and default it to current date.
var userSchema = new Schema({
  password: {type:String, minlength: 5, maxlength: 15}
  createdAt: {type:date, default: new Date()}
})
