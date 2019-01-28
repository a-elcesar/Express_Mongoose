var express=require('express')
var routes=require('./routes')
var app=express()
app.use(routes)

app.get('/',(req,res)=>{
    res.send(`<h1>Express ♥ MongoDB</h1>
    <h3>Please use Postman to post data</h3>
    <h3>Please go to /data to GET</h3>`)
})

app.listen(1247,()=>{console.log('Server running on port 1247')})