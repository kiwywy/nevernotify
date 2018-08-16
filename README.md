# Never Notify

You can use this API to send message alerts for the Line group. 
Your message will be saved after the message is delivered. 
*You can view the history from http://nmis.evergreen.com.tw:9000/.*

## API Parameters [/api/{sendto}/{sendfm}/{message}]
+ `sendto` Select Your Dept from *SYM-SY1,SYM-SY2,SYM-SY3,SYM-SY4,SYM-SY5,SYM-SSV,SYM-COM,SYM-TSM,UHD*
+ `sendfm` Please enter your **Server Name** or **Application Name** or **AD Number**.
+ `message` String type without html code.

# Start to Use API
OK, `Never Notify` probably isn't the best name for our resource but it will do
for now. Note the URI `/api` is enclosed in square brackets.

### Retrieve a Message [GET]
Now this is informative! No extra explanation needed here. This action clearly
retrieves the message.

+ Response `405` (application/x-www-form-urlencoded)
<pre>
{ "status":405,"message":"Method Not Allowed" }
</pre>
### Send a Message [POST]
`Send a message` - nice and simple naming is the best way to go.
+ Parameters
    + sendto(string) - Select Your Dept from *SYM-SY1,SYM-SY2,SYM-SY3,SYM-SY4,SYM-SY5,SYM-SSV,SYM-COM,SYM-TSM,UHD*
    + sendfm(string) - Please enter your **Server Name** or **Application Name** or **AD Number**.
    + message(string) - String type without html code.   
    
+ Request (application/x-www-form-urlencoded) 

+ Response `200` (application/x-www-form-urlencoded)

    + Body

            {
                "status":200,
                "message":"ok"
            }
        
+ Response `400` (application/x-www-form-urlencoded)

    + Body

            {
                "status":400,
                "message":"sendto: may not be empty"
            }
        
+ Response `410` (application/x-www-form-urlencoded)

    + Body

            {
                "status":410,
                "message":"sendfm: may not be empty"
            }
        
+ Response `420` (application/x-www-form-urlencoded)

    + Body

            {
                "status":420,
                "message":"message: may not be empty"
            }
        
+ Response `500` (application/x-www-form-urlencoded)

    + Body

            {
                "status":500,
                "message":"sendto: no group can select"
            }
