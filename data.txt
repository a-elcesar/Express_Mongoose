var mongoose=require('mongoose')
var Schema=mongoose.Schema

var template=new Schema({
    namacpu:String,
    tipe:String,
    platform:String,
    rilis:String,
    ramSisa:Number,
    ramTotal:Number
})

var Data=mongoose.model('data',template)

module.exports=Data