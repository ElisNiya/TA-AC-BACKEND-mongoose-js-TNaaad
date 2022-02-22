writeCode

Q.create a user schema with following fields and type
1.name -> string
2.email -> string
3.age -> number

Q. update user schema to make email lowercase and default age to be 0.

var userSchema = new Schema({
  name : String,
  email : {type:String, lowercase:true}
  age : {type: Number, default: 0 }
})
