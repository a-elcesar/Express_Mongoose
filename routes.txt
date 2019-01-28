var router=require('express').Router()
var mongoose=require('mongoose')
var Data=require('./models/data')
var url='mongodb://elcesar:1234@localhost/dataCPU'
var os=require('os')

mongoose.connect(url,{useNewUrlParser:true},()=>{
    console.log('Connected to MongoDB')
})

//Route utk POST ke /data
router.post('/data',(req,res)=>{
    new Data({
        namacpu:os.hostname(),
        tipe:os.type(),
        platform:os.platform(),
        rilis:os.release(),
        ramSisa:os.freemem(),
        ramTotal:os.totalmem()
    }).save().then((x)=>{
        res.send({sent:x})
    })
})
/*
POST ke localhost:1247/data
Body > Raw > JSON > {"namacpu":""}
Akan terkirim property lain beserta value nya secara otomatis
*/

//Route utk GET dari /data
router.get('/data',(req,res)=>{
    Data.find((err,result)=>{
        res.send(result)
    })
})

module.exports=router