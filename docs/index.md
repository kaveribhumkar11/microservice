# Description
    This microservice will help your project to set up video calls for users. 
    Currently we are supporting google(hangout) meetings and zoom meetings. 
# Microservice Overview through Diagram
<figure>
  <img src="https://github.com/kaveribhumkar11/microservice/blob/master/docs/images/image1.png" width="300" />
  <figcaption>Microservice Overview</figcaption>
</figure>

# Steps to Integrate/use this microservice in your system
* For now, you will need to mail me the details like your product name along with the redirect url(redirect url will be used while connecting the user of your project with this microservice). My mail id = kaveri.bhumkar@plus91.in
* When you complete the above step, you will receive client_key in response using which you will be able to use the microservice’s apis(features).
# Response status codes and their meaning
    200: OK(default)
    204: Content not found
    400: Bad request
    412: Precondition Failed(The precondition given in the request evaluated to false by the server)
    422: Parameters not found 
    500: Internal server error
# APIs
Note : timestamps to be considered IST(Asia/Kolkata)
# API List
## Call to Connect User Account
### Request Parameters
<html>
<body><table><tbody><tr><td colspan="1" rowspan="1"><p ><span >Key</span></p></td><td colspan="1" rowspan="1"><p ><span >Type</span></p></td><td colspan="1" rowspan="1"><p ><span >Is Mandatory?</span></p></td></tr><tr><td colspan="1" rowspan="1"><p ><span >client_key</span></p></td><td colspan="1" rowspan="1"><p ><span >String</span></p></td><td colspan="1" rowspan="1"><p ><span >Yes</span></p></td></tr><tr><td colspan="1" rowspan="1"><p ><span >user_id</span></p></td><td colspan="1" rowspan="1"><p ><span >String</span></p></td><td colspan="1" rowspan="1"><p ><span >Yes</span></p></td></tr><tr><td colspan="1" rowspan="1"><p ><span >connection_type</span></p></td><td colspan="1" rowspan="1"><p ><span >Integer</span></p></td><td colspan="1" rowspan="1"><p ><span >Yes</span></p></td></tr></tbody></table></body></html>

### Response Parameters
<html><body>
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>status</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iAccountId</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>expires_on</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Date</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>connection_type</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>user_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>
</body></html>

### Request and Response object and example
<html><body>
<table class="c56"><tbody><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span class="c28">https://services.medixcel.in/connect</span><span>/connectUserAccount.php</span></p></td></tr><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span>GET</span></p></td></tr><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span>client_key&lt;client_key given at the time of client registration&gt;,</span></p><p ><span>user_id&lt;unique id of the user of the client&gt;,</span></p><p ><span>connection_type&lt;1(zoom),2(google)&gt;</span></p></td></tr><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span>status&lt;success/error&gt;, iAccountId&lt;Will be used to set up meeting&gt;,expires_on&lt;connection expiry date when user do not request for set_up_meeting for 6 months straight&gt;</span></p></td></tr><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span class="c49 c28"><a class="c10" href="https://www.google.com/url?q=https://services.medixcel.in/connect/connectUserAccount.php?client_key%3Dmedixcel_lite%26user_id%3D16%26connection_type%3D2&amp;sa=D&amp;ust=1599809928979000&amp;usg=AOvVaw1ugrOF7nYMxsGTAJg-gddI">https://services.medixcel.in/connect/connectUserAccount.php?client_key=medixcel_lite&amp;user_id=16&amp;connection_type=2</a></span></p></td></tr><tr class="c15"><td class="c36" colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td class="c26" colspan="1" rowspan="1"><p ><span>status=success, iAccountId=35, expires_on=2020-12-21 22:25:30</span></p></td></tr></tbody></table>
</body></html>

### PHP Sample Code
    <?php
     header('Location: ' .”https://services.medixcel.in/connect/connectUserAccount.php?client_key=medixcel_lite&user_id=2&connection_type=2”);
    ?>

### NodeJs Sample Code
    return res.redirect(”https://services.medixcel.in/connect/connectUserAccount.php?client_key=medixcel_lite&user_id=2&connection_type=2”);
## Call to Schedule Meeting
### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>video_call_provider_account_id</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>duration_in_minutes</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>meeting_title</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>participants</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>Array of Objects</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c2"><td class="c29" colspan="1" rowspan="1"><p ><span>iUserID</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>No</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>sEmail</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>Email</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>sFirstName</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>No</span></p></td></tr><tr class="c15"><td class="c29" colspan="1" rowspan="1"><p ><span>sLastName</span></p></td><td class="c23" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>No</span></p></td></tr></tbody></table>

### Response Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>connection_type</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>request_recieved</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Request Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_summary</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Summary Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iMeetingId</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingUID</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sHostMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>dAddedOn</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingTitle</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sStartTime</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iDuration</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_object</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/set_up_meeting</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&quot;video_call_provider_account_id&quot;:&lt;Account id you received while connecting user account&gt;,</span></p><p ><span>&quot;duration_in_minutes&quot;:&lt;duration_in_minutes&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;meeting_title&quot; : &lt;meeting title&gt;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;participants&quot;:[{</span></p><p ><span>&quot;iUserID&quot;:&lt;UId&gt;,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></p><p ><span>&quot;sEmail&quot;:&lt;email id of attendee&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;sFirstName&quot;:&lt;first name of the attendee&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;sLastName&quot;:&lt;last name of the attendee&gt;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}]</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &lt;1(zoom),2(google)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;request_recieved&quot;: &lt;request object&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &ldquo;iMeetingId&rdquo;:&lt;Meeting Id&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &lt;Meeting UID&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &lt;Meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &lt;host meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &lt;Request received on(date)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &lt;Meeting title&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &lt;meeting start time&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &lt;duration in minutes&gt;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: &lt;Meeting object&gt;</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &lt;response status code&gt;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &lt;Response message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;video_call_provider_account_id&quot;:&quot;35&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;duration_in_minutes&quot;:&quot;60&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_title&quot; : &quot;Testing&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;participants&quot;:[{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;iUserID&quot;:&quot;&quot;,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;sEmail&quot;:&quot;kaveri.bhumkar24@gmail.com&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;sFirstName&quot;:&quot;Kaveri&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;sLastName&quot;:&quot;Bhumkar&quot;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}]</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;request_recieved&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;client_key&quot;: &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;actionName&quot;: &quot;set_up_meeting&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;video_call_provider_account_id&quot;: &quot;35&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;duration_in_minutes&quot;: &quot;60&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_title&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;participants&quot;: &quot;[{\&quot;iUserID\&quot;:\&quot;\&quot;,\&quot;sEmail\&quot;:\&quot;kaveri.bhumkar24@gmail.com\&quot;,\&quot;sFirstName\&quot;:\&quot;Kaveri\&quot;,\&quot;sLastName\&quot;:\&quot;Bhumkar\&quot;}]&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iMeetingID&quot;: 45,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &quot;60&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;kind&quot;: &quot;calendar#event&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;etag&quot;: &quot;\&quot;3185517172314000\&quot;&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;id&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: &quot;confirmed&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;htmlLink&quot;: &quot;https://www.google.com/calendar/event?eid=Z3FmY2lta2w5am0ydTdwM2c4dHYxcW00dWsga2F2ZXJpLmJodW1rYXJAcGx1czkxLmlu&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;created&quot;: &quot;2020-06-21T16:56:26.000Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;updated&quot;: &quot;2020-06-21T16:56:26.157Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;summary&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;creator&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;organizer&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;start&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T22:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;end&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T23:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iCalUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk@google.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sequence&quot;: 0,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;attendees&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar24@gmail.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;displayName&quot;: &quot;Kaveri Bhumkar&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;responseStatus&quot;: &quot;needsAction&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;hangoutLink&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceData&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;createRequest&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;requestId&quot;: &quot;db9b05086b5e8cd8afdd38f9209edded&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolutionKey&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;statusCode&quot;: &quot;success&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPoints&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;video&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;meet.google.com/znr-yxrc-xoc&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;regionCode&quot;: &quot;US&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;phone&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;tel:+1-720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;+1 720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;pin&quot;: &quot;880848705&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolution&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;key&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;name&quot;: &quot;Google Meet&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iconUri&quot;: &quot;https://lh5.googleusercontent.com/proxy/bWvYBOb7O03a7HK5iKNEAPoUNPEXH1CHZjuOkiqxHx8OtyVn9sZ6Ktl8hfqBNQUUbCDg6T2unnsHx7RSkCyhrKgHcdoosAW8POQJm_ZEvZU9ZfAE7mZIBGr_tDlF8Z_rSzXcjTffVXg3M46v&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceId&quot;: &quot;znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;signature&quot;: &quot;ADR/mfOqKiVmLGEBmIzZxN4nH+H3&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;reminders&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;useDefault&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
    //Request Data
    $aData = array(
        "client_key" =>"medixcel_lite",
        "video_call_provider_account_id" => "115",
        "start_time":"2020-07-04 23:30:01",
        "duration_in_minutes"=>"20",
        "meeting_title" => "Testing that",
        "participants"=>[array(
                    "iUserID"=>"",  
                    "sEmail"=>"kaveri.bhumkar@plus91.in",
                    "sFirstName"=>"Kaveri",
                    "sLastName"=>"Bhumkar"
                ),
                array(
                    "iUserID"=>"",  
                    "sEmail"=>"sagar.padalghare@plus91.in",
                    "sFirstName"=>"Sagar",
                    "sLastName"=>"Padalghare"
                )
            ]
        );
    // API URL
    $url='https://services.medixcel.in/connect/reschedule_meeting';
    // Create a new cURL resource
    $ch = curl_init($url);
 
    $payload = json_encode($aData);
    // Attach encoded JSON string to the POST fields
    curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
 
    // Set the content type to application/json
    curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
 
    // Return response instead of outputting
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
 
    // Execute the POST request
    $result = curl_exec($ch);
 
    // Close cURL resource
    if (curl_errno($ch)) {
        $error_msg = curl_error($ch);
    }
    curl_close($ch);
    if (isset($error_msg)) {
        //Handle cURL error accordingly
        var_dump($error_msg);
    }
    //Print Result
    var_dump($result);        
?>

### NodeJs Sample Code
    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    let participants = [{
            iUserID:"", 
            sEmail:"kaveri.bhumkar@plus91.in",
            sFirstName:"Kaveri",
            sLastName:"Bhumkar"
        },
        {
            iUserID:"", 
            sEmail:"sagar.padalghare@plus91.in",
            sFirstName:"Sagar",
            sLastName:"Padalghare"
        }];
        
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("video_call_provider_account_id","115");
    params.append("start_time","2020-07-04 23:30:01");
    params.append("duration_in_minutes","20");
    params.append("meeting_title","Testing that");
    aParticipants = JSON.stringify(participants);
    params.append("participants",aParticipants);
    fetch('https://services.medixcel.in/connect/schedule_meeting', { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));

## Call to Get all Meetings of Client for Date
### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>date</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Date</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>user_id</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>No</span></p></td></tr></tbody></table>

### Response Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meetings_for_date</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Date</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>total_meetings</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meetings</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Array of Meetings Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>connection_type</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>user_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_url</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_start_time</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_duration</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_added_on</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/get_meetings_of_client_for_date</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;date&quot; : &lt;Date in YYYY-MM-DD format&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &ldquo;user_id&rdquo; : &lt;unique id of the user from client side(optional)&gt; </span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;output&quot; : {</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meetings_for_date&quot; : &lt;Date in YYYY-MM-DD format&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;total_meetings&quot; : &lt;Total number of meetings found for the date&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meetings&quot; : [</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;connection_type : &lt;1(Zoom),2(Google)&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;user_id : &lt;Unique id of the user which makes it unique on client side&gt;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; meeting_id : &lt;Meeting id&gt;, </span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;meeting_url : &lt;Meeting Url&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;meeting_start_time : &lt;Meeting Start Time&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;meeting_duration : &lt;Duration of the meeting&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;meeting_added_on : &lt;Date and time of meeting added&gt;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;] </span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;response_status_code&quot;:&lt;Response status code&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;msg&quot; : &lt;Response Message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;date&quot; : &quot;2020-06-15&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot; : &quot;&quot; </span></p><p ><span>}</span></p><p class="c7 c14"><span></span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meetings_for_date&quot;: &quot;2020-06-15&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;total_meetings&quot;: 9,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meetings&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;10&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/mww-ixyc-skm&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 08:55:59&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 08:55:59&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;11&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/ajg-onez-yth&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 09:23:02&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 09:23:02&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;12&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/qnx-rogw-zjb&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 09:24:50&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 09:24:50&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;13&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/uwo-rrfa-mdp&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 10:08:20&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 10:08:20&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;14&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/kdc-ozwk-kdi&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 10:13:40&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 10:13:40&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;29&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/cfn-pdmr-xnc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 17:26:56&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 17:26:56&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/vxc-arzb-vpo&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 17:28:35&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 17:28:35&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;4&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;31&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/yqg-jmjc-cxt&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 18:25:33&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 18:25:33&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;user_id&quot;: &quot;4&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;32&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_url&quot;: &quot;https://meet.google.com/jfg-smcm-bfi&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_duration&quot;: &quot;30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_start_time&quot;: &quot;2020-06-15 18:30:20&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_added_on&quot;: &quot;2020-06-15 18:30:20&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; ]</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
        //Request Data
        $aData = array(
            "client_key" =>"medixcel_lite",
            "date" => "2020-06-15"
            );
        // API URL
        $url='https://services.medixcel.in/connect/get_meetings_of_client_for_date';
        // Create a new cURL resource
        $ch = curl_init($url);
    
        $payload = json_encode($aData);
        // Attach encoded JSON string to the POST fields
        curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
    
        // Set the content type to application/json
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
    
        // Return response instead of outputting
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    
        // Execute the POST request
        $result = curl_exec($ch);
    
        // Close cURL resource
        if (curl_errno($ch)) {
            $error_msg = curl_error($ch);
        }
        curl_close($ch);
        if (isset($error_msg)) {
            //Handle cURL error accordingly
            var_dump($error_msg);
        }
        //Print Result
        var_dump($result);        
    ?>

### NodeJs Sample Code

    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("date","2020-06-15");
    fetch('https://services.medixcel.in/connect/get_meetings_of_client_for_date, { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));

## Call to Disconnect User Account
<table class="c24"><tbody><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>account_id</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr></tbody></table>

### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>disconnected_account_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Response Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>disconnected_account_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/disconnect_user_account</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;account_id&quot; : &lt;Account id you received while connecting user account&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;output&quot; : {</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;disconnected_account_id&quot; : &lt;Account id of the disconnected user&gt;</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;response_status_code&quot;:&lt;Response status code&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;msg&quot; : &lt;Response Message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;account_id&quot; : &quot;34&quot;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;disconnected_user_account&quot;: &quot;34&quot;</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
        //Request Data
        $aData = array(
            "client_key" =>"medixcel_lite",
            "account_id" => "115"
            );
        // API URL
        $url='https://services.medixcel.in/connect/cancel_meeting';
        // Create a new cURL resource
        $ch = curl_init($url);
    
        $payload = json_encode($aData);
        // Attach encoded JSON string to the POST fields
        curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
    
        // Set the content type to application/json
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
    
        // Return response instead of outputting
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    
        // Execute the POST request
        $result = curl_exec($ch);
    
        // Close cURL resource
        if (curl_errno($ch)) {
            $error_msg = curl_error($ch);
        }
        curl_close($ch);
        if (isset($error_msg)) {
            //Handle cURL error accordingly
            var_dump($error_msg);
        }
        //Print Result
        var_dump($result);        
    ?>

### NodeJs Sample Code

    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("account_id","115");
    fetch('https://services.medixcel.in/connect/disconnect_user_account', { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));

## Call to Get Meeting Info
### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>meeting_id</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr></tbody></table>

### Response Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>connection_type</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_summary</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Summary Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iMeetingId</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingUID</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sHostMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>dAddedOn</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingTitle</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sStartTime</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iDuration</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_object</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/get_meeting_details</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &lt;meeting id&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp;&quot;meeting_id&quot;: &lt;Meeting Id&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &lt;1(zoom),2(google)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &lt;Meeting UID&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &lt;Meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &lt;host meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &lt;Request received on(date)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &lt;Meeting title&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &lt;meeting start time&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &lt;duration in minutes&gt;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: &lt;Meeting object&gt;</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &lt;response status code&gt;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &lt;Response message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &quot;45&quot;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iMeetingID&quot;: &quot;45&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &quot;60&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;kind&quot;: &quot;calendar#event&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;etag&quot;: &quot;\&quot;3185517172314000\&quot;&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;id&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: &quot;confirmed&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;htmlLink&quot;: &quot;https://www.google.com/calendar/event?eid=Z3FmY2lta2w5am0ydTdwM2c4dHYxcW00dWsga2F2ZXJpLmJodW1rYXJAcGx1czkxLmlu&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;created&quot;: &quot;2020-06-21T16:56:26.000Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;updated&quot;: &quot;2020-06-21T16:56:26.157Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;summary&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;creator&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;organizer&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;start&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T22:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;end&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T23:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iCalUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk@google.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sequence&quot;: 0,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;attendees&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar24@gmail.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;displayName&quot;: &quot;Kaveri Bhumkar&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;responseStatus&quot;: &quot;needsAction&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;hangoutLink&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceData&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;createRequest&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;requestId&quot;: &quot;db9b05086b5e8cd8afdd38f9209edded&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolutionKey&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;statusCode&quot;: &quot;success&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPoints&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;video&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;meet.google.com/znr-yxrc-xoc&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;regionCode&quot;: &quot;US&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;phone&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;tel:+1-720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;+1 720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;pin&quot;: &quot;880848705&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolution&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;key&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;name&quot;: &quot;Google Meet&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iconUri&quot;: &quot;https://lh5.googleusercontent.com/proxy/bWvYBOb7O03a7HK5iKNEAPoUNPEXH1CHZjuOkiqxHx8OtyVn9sZ6Ktl8hfqBNQUUbCDg6T2unnsHx7RSkCyhrKgHcdoosAW8POQJm_ZEvZU9ZfAE7mZIBGr_tDlF8Z_rSzXcjTffVXg3M46v&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceId&quot;: &quot;znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;signature&quot;: &quot;ADR/mfOqKiVmLGEBmIzZxN4nH+H3&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;reminders&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;useDefault&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
        //Request Data
        $aData = array(
            "client_key" =>"medixcel_lite",
            "meeting_id" => "115"
            );
        // API URL
        $url='https://services.medixcel.in/connect/get_meeting_details';
        // Create a new cURL resource
        $ch = curl_init($url);
    
        $payload = json_encode($aData);
        // Attach encoded JSON string to the POST fields
        curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
    
        // Set the content type to application/json
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
    
        // Return response instead of outputting
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    
        // Execute the POST request
        $result = curl_exec($ch);
    
        // Close cURL resource
        if (curl_errno($ch)) {
            $error_msg = curl_error($ch);
        }
        curl_close($ch);
        if (isset($error_msg)) {
            //Handle cURL error accordingly
            var_dump($error_msg);
        }
        //Print Result
        var_dump($result);        
    ?>

### NodeJs Sample Code
    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("meeting_id","115");
    fetch('https://services.medixcel.in/connect/get_meeting_details', { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));
## Call to Cancel Meeting 
### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>meeting_id</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr></tbody></table>

### Response Parameters
<table class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>cancelled_meeting_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/cancel_meeting</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &lt;meeting id&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp;&quot;cancelled_meeting_id&quot;: &lt;Meeting Id&gt;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &lt;response status code&gt;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &lt;Response message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example </span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &quot;45&quot;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;cancelled_meeting_id&quot;: &quot;45&quot;</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
        //Request Data
        $aData = array(
            "client_key" =>"medixcel_lite",
            "meeting_id" => "115"
            );
        // API URL
        $url='https://services.medixcel.in/connect/cancel_meeting';
        // Create a new cURL resource
        $ch = curl_init($url);
    
        $payload = json_encode($aData);
        // Attach encoded JSON string to the POST fields
        curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
    
        // Set the content type to application/json
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
    
        // Return response instead of outputting
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    
        // Execute the POST request
        $result = curl_exec($ch);
    
        // Close cURL resource
        if (curl_errno($ch)) {
            $error_msg = curl_error($ch);
        }
        curl_close($ch);
        if (isset($error_msg)) {
            //Handle cURL error accordingly
            var_dump($error_msg);
        }
        //Print Result
        var_dump($result);        
    ?>

### NodeJs Sample Code
    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("meeting_id","115");
    fetch('https://services.medixcel.in/connect/cancel_meeting', { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));

## Call to Reschedule Meeting 
### Request Parameters
<table class="c24"><tbody><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Type</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Is Mandatory?</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>client_key</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>String</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>meeting_id</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>start_time</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr><tr class="c15"><td class="c17" colspan="1" rowspan="1"><p ><span>duration_in_minutes</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Integer</span></p></td><td class="c17" colspan="1" rowspan="1"><p ><span>Yes</span></p></td></tr></tbody></table>

### Response Parameters
<table 
class="c24"><tbody><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>Key</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Type</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>output</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Output Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>rescheduled_meeting_id</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>connection_type</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>request_recieved</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Request Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_summary</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Summary Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iMeetingId</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingUID</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sHostMeetingURL</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>dAddedOn</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sMeetingTitle</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>sStartTime</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>DateTime</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>iDuration</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>meeting_object</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Meeting Object</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>response_status_code</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>Integer</span></p></td></tr><tr class="c15"><td class="c5" colspan="1" rowspan="1"><p ><span>msg</span></p></td><td class="c5" colspan="1" rowspan="1"><p ><span>String</span></p></td></tr></tbody></table>

### Request and Response object and example
<p class="c21 c14"><span></span></p><a id="t.bc7202572887043f9ac2f0ff715114570f8c51b8"></a><a id="t.32"></a>

<table class="c39"><tbody><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Url</span></p></td><td colspan="1" rowspan="1"><p class="c7 c54"><span>https://services.medixcel.in/connect/reschedule_meeting</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Method</span></p></td><td colspan="1" rowspan="1"><p ><span>POST</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request parameter</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &lt;client_key&gt;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &lt;meeting id&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&ldquo;start_time&rdquo;: &lt;meeting start time&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&ldquo;duration_in_minutes&rdquo; : &lt;duration in minutes&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Expected response</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp;&quot;rescheduled_meeting_id&quot;: &lt;Meeting Id&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &lt;1(zoom),2(google)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;request_recieved&quot;: &lt;request object&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &lt;Meeting UID&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &lt;Meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &lt;host meeting url&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &lt;Request received on(date)&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &lt;Meeting title&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &lt;meeting start time&gt;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &lt;duration in minutes&gt;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: &lt;Meeting object&gt;</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &lt;response status code&gt;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &lt;Response message&gt;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Request Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;client_key&quot; : &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;meeting_id&quot; : &quot;45&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;start_time&quot;:&quot;2020-06-22 01:01:01&quot;,</span></p><p ><span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&quot;duration_in_minutes&quot;:&quot;60&quot;</span></p><p ><span>}</span></p></td></tr><tr class="c15"><td  colspan="1" rowspan="1"><p ><span>Response Example</span></p></td><td colspan="1" rowspan="1"><p ><span>{</span></p><p ><span>&nbsp; &nbsp; &quot;output&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;rescheduled_meeting_id&quot;: &quot;45&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;connection_type&quot;: &quot;2&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;request_recieved&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;client_key&quot;: &quot;medixcel_lite&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;actionName&quot;: &quot;reschedule_meeting&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_id&quot;: &quot;45&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;start_time&quot;: &quot;2020-06-22 01:01:01&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;duration_in_minutes&quot;: &quot;60&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_summary&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iMeetingID&quot;: &quot;45&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sHostMeetingURL&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dAddedOn&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sMeetingTitle&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sStartTime&quot;: &quot;2020-06-21 22:26:25&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iDuration&quot;: &quot;60&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &quot;meeting_object&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;kind&quot;: &quot;calendar#event&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;etag&quot;: &quot;\&quot;3185517172314000\&quot;&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;id&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: &quot;confirmed&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;htmlLink&quot;: &quot;https://www.google.com/calendar/event?eid=Z3FmY2lta2w5am0ydTdwM2c4dHYxcW00dWsga2F2ZXJpLmJodW1rYXJAcGx1czkxLmlu&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;created&quot;: &quot;2020-06-21T16:56:26.000Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;updated&quot;: &quot;2020-06-21T16:56:26.157Z&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;summary&quot;: &quot;Testing&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;creator&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;organizer&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar@plus91.in&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;self&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;start&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T22:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;end&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;dateTime&quot;: &quot;2020-06-21T23:26:25+05:30&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;timeZone&quot;: &quot;Asia/Kolkata&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iCalUID&quot;: &quot;gqfcimkl9jm2u7p3g8tv1qm4uk@google.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;sequence&quot;: 0,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;attendees&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;email&quot;: &quot;kaveri.bhumkar24@gmail.com&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;displayName&quot;: &quot;Kaveri Bhumkar&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;responseStatus&quot;: &quot;needsAction&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;hangoutLink&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceData&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;createRequest&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;requestId&quot;: &quot;db9b05086b5e8cd8afdd38f9209edded&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolutionKey&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;status&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;statusCode&quot;: &quot;success&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPoints&quot;: [</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;video&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;https://meet.google.com/znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;meet.google.com/znr-yxrc-xoc&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;regionCode&quot;: &quot;US&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;entryPointType&quot;: &quot;phone&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;uri&quot;: &quot;tel:+1-720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;label&quot;: &quot;+1 720-580-1188&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;pin&quot;: &quot;880848705&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ],</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceSolution&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;key&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;type&quot;: &quot;hangoutsMeet&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;name&quot;: &quot;Google Meet&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;iconUri&quot;: &quot;https://lh5.googleusercontent.com/proxy/bWvYBOb7O03a7HK5iKNEAPoUNPEXH1CHZjuOkiqxHx8OtyVn9sZ6Ktl8hfqBNQUUbCDg6T2unnsHx7RSkCyhrKgHcdoosAW8POQJm_ZEvZU9ZfAE7mZIBGr_tDlF8Z_rSzXcjTffVXg3M46v&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;conferenceId&quot;: &quot;znr-yxrc-xoc&quot;,</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;signature&quot;: &quot;ADR/mfOqKiVmLGEBmIzZxN4nH+H3&quot;</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;reminders&quot;: {</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;useDefault&quot;: true</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; &nbsp; &nbsp; }</span></p><p ><span>&nbsp; &nbsp; },</span></p><p ><span>&nbsp; &nbsp; &quot;response_status_code&quot;: &quot;200&quot;,</span></p><p ><span>&nbsp; &nbsp; &quot;msg&quot;: &quot;success&quot;</span></p><p ><span>}</span></p></td></tr></tbody></table>

### PHP Sample Code
    <?php
        //Request Data
        $aData = array(
            "client_key" =>"medixcel_lite",
            "meeting_id" => "115",
            "start_time":"2020-07-04 23:30:01",
            "duration_in_minutes"=>"20",
            "meeting_title" => "Testing that",
            "participants"=>[array(
                        "iUserID"=>"",  
                        "sEmail"=>"kaveri.bhumkar@plus91.in",
                        "sFirstName"=>"Kaveri",
                        "sLastName"=>"Bhumkar"
                    ),
                    array(
                        "iUserID"=>"",  
                        "sEmail"=>"sagar.padalghare@plus91.in",
                        "sFirstName"=>"Sagar",
                        "sLastName"=>"Padalghare"
                    )
                ]
            );
        // API URL
        $url='https://services.medixcel.in/connect/reschedule_meeting';
        // Create a new cURL resource
        $ch = curl_init($url);
    
        $payload = json_encode($aData);
        // Attach encoded JSON string to the POST fields
        curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
    
        // Set the content type to application/json
        curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-Type:application/json'));
    
        // Return response instead of outputting
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    
        // Execute the POST request
        $result = curl_exec($ch);
    
        // Close cURL resource
        if (curl_errno($ch)) {
            $error_msg = curl_error($ch);
        }
        curl_close($ch);
        if (isset($error_msg)) {
            //Handle cURL error accordingly
            var_dump($error_msg);
        }
        //Print Result
        var_dump($result);        
    ?>

### NodeJs Sample Code
    const express = require('express');
    const bodyParser = require('body-parser');
    const fetch = require('node-fetch');
    const { URLSearchParams } = require('url');
    const app = express();
    
    app.use(express.static('public'));
    app.use(bodyParser.urlencoded({ extended: false }));
    app.use(bodyParser.json());
    
    app.use(function(req, res, next) {
    res.header("Access-Control-Allow-Origin", "*");
    res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
    next();
    });
    let participants = [{
            iUserID:"", 
            sEmail:"kaveri.bhumkar@plus91.in",
            sFirstName:"Kaveri",
            sLastName:"Bhumkar"
        },
        {
            iUserID:"", 
            sEmail:"sagar.padalghare@plus91.in",
            sFirstName:"Sagar",
            sLastName:"Padalghare"
        }];
        
    app.set('trust proxy', true);
    const params = new URLSearchParams(); //params to pass whill making fetch call to interface file
    params.append("client_key","medixcel_lite");
    params.append("meeting_id","115");
    params.append("start_time","2020-07-04 23:30:01");
    params.append("duration_in_minutes","20");
    params.append("meeting_title","Testing that");
    aParticipants = JSON.stringify(participants);
    params.append("participants",aParticipants);
    fetch('https://services.medixcel.in/connect/reschedule_meeting', { method: 'POST', body: params })
    .then(res => res.json())
    .then(json => {
        console.log(json);
    })
    .catch(error => { // catch the error caused by error in interface code
    // log the error
    console.log(error);
    });
    const port=3005;
    app.listen(port,()=>console.log(`Listening to port ${port}`));
