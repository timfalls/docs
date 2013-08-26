---
layout: page
weight: 0
title: Invalid Emails
navigation:
  show: true
---

This endpoint allows you to retrieve and delete entries in the Invalid Emails list.


{% anchor h2 %} get {% endanchor %}


Retrieve a list of invalid emails with addresses and response codes, optionally with dates.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>date</td>
         <td>No</td>
         <td>Must be set to 1</td>
         <td>Retrieve the timestamp of the invalid email records. It will return a date in a MySQL timestamp format - YYYY-MM-DD HH:MM:SS</td>
      </tr>
      <tr>
         <td>days</td>
         <td>No</td>
         <td>If specified, must be an integer greater than 0</td>
         <td>Number of days in the past for which to retrieve invalid emails (includes today)</td>
      </tr>
      <tr>
         <td>start_date</td>
         <td>No</td>
         <td>Date must be in YYYY-MM-DD format and be earlier than the end_date parameter.</td>
         <td>The start of the date range for which to retrieve invalid emails.</td>
      </tr>
      <tr>
         <td>end_date</td>
         <td>No</td>
         <td>Date must be in YYYY-MM-DD format and be later than the start_date parameter.</td>
         <td>The end of the date range for which to retrieve invalid emails.</td>
      </tr>
      <tr>
         <td>limit</td>
         <td>No</td>
         <td>some integer</td>
         <td>Optional field to limit the number of results returned.</td>
      </tr>
      <tr>
         <td>offset</td>
         <td>No</td>
         <td>some integer</td>
         <td>Optional beginning point in the list to retrieve from.</td>
      </tr>
      <tr>
         <td>email</td>
         <td>No</td>
         <td>email address eg testing@example.com</td>
         <td>Optional email addresses to search for.</td>
      </tr>
   </tbody>
</table>

{% xmljsontabs get %}

<div class="tab-content">
<div class="tab-pane active" id="get-json">
### Call

{% codeblock %} https://sendgrid.com/api/invalidemails.get.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&date=1 {% endcodeblock %}

### Response


{% codeblock lang:javascript %}
[
  {
    "reason": "Known bad domain",
    "created": "2011-06-06 16:11:57",
    "email": "test@example.com"
  },
  {
    "reason": "Invalid address",
    "created": "2012-08-17 11:04:38",
    "email": "brandon"
  }
]
{% endcodeblock %}


</div>
<div class="tab-pane" id="get-xml">
### Call

{% codeblock %} https://sendgrid.com/api/invalidemails.get.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&date=1 {% endcodeblock %}

### Response


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<invalidemails>
   <invalidemail>
      <reason>Known bad domain</reason>
      <created>2011-06-06 16:11:57</created>
      <email>test@example.com</email>
   </invalidemail>
   <invalidemail>
      <reason>Invalid address</reason>
      <created>2012-08-17 11:04:38</created>
      <email>brandon</email>
   </invalidemail>
</invalidemails>

{% endcodeblock %}


</div>
</div>

* * * * *


{% anchor h2 %} delete {% endanchor %}


Delete an address from the Invalid Email list.

<table class="table table-bordered table-striped">
   <tbody>
      <tr>
         <th>Parameter</th>
         <th>Required</th>
         <th>Requirements</th>
         <th>Description</th>
      </tr>
      <tr>
         <td>email</td>
         <td>Yes</td>
         <td>Must be a valid user account email</td>
         <td>Email Invalid Email address to remove</td>
      </tr>
      <tr/>
   </tbody>
</table>

{% xmljsontabs delete %}

<div class="tab-content">
<div class="tab-pane active" id="delete-json">
### Call

{% codeblock %} https://sendgrid.com/api/invalidemails.delete.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&email=emailToDelete@domain.com {% endcodeblock %}

### Response: Success


{% codeblock lang:javascript %}
{
  "message": "success"
}
{% endcodeblock %}


### Response: Error


{% codeblock lang:javascript %}
{
  "message": "error",
  "errors": [
    "...error messages..."
  ]
}
{% endcodeblock %}


</div>
<div class="tab-pane" id="delete-xml">
### Call

{% codeblock %} https://sendgrid.com/api/invalidemails.delete.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&email=emailToDelete@domain.com {% endcodeblock %}

### Response: Success

{% codeblock %} <result> success <result> {% endcodeblock %}

### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result> Email does not exist @nodes </result>

{% endcodeblock %}


</div>
</div>
