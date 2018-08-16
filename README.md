# Never Notify

You can use this API to send message alerts for the Line group. 
Your message will be saved after the message is delivered. 
*You can view the history from http://localhost/history.*

## API Parameters [/api]
+ `sendto(string)` Select Your Dept
+ `sendfm(string)` Please enter your **Server Name** or **Application Name** or **AD Number**.
+ `message(string)` String type without html code.

# Start to Use API
OK, `Never Notify` probably isn't the best name for our resource but it will do
for now. Note the URI `/api` is enclosed in square brackets.

### Retrieve a Message [GET]
Now this is informative! No extra explanation needed here. This action clearly
retrieves the message.

+ Response `405` (application/x-www-form-urlencoded)
	<pre><code class="json">{ "status":405,"message":"Method Not Allowed" }</code></pre>

### Send a Message [POST]
`Send a message` - nice and simple naming is the best way to go.

+ Response `200` (application/x-www-form-urlencoded)
	<pre><code class="json">{ "status":200,"message":"ok" }</code></pre>
        
+ Response `400` (application/x-www-form-urlencoded)
    <pre><code class="json">{ "status":400,"message":"sendto: may not be empty" }</code></pre>
        
+ Response `410` (application/x-www-form-urlencoded)
    <pre><code class="json">{ "status":410,"message":"sendfm: may not be empty" }</code></pre>
        
+ Response `420` (application/x-www-form-urlencoded)
    <pre><code class="json">{ "status":420,"message":"message: may not be empty" }</code></pre>
        
+ Response `500` (application/x-www-form-urlencoded)
    <pre><code class="json">{ "status":500,"message":"sendto: no group can select" }</code></pre>

## Sample from AJAX
<pre><code class="javascript">function testAPI(){
  $.ajax({
      async: true,
      cache: false,
      type:'POST',
      url:'http://localhost/api',
      dataType:'json',
      data:{
        message:"Hello",
        sendto: "DEPT",
        sendfm: "KIWY"
       },
      success:function(data){
        console.log(data);
      }, error:function(err){
        console.log(err);
      }
  });

  }</code></pre>
