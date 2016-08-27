dom-injector-js
=====================
Read Me
=====================
## About
domInjector is a simple jQuery plugin to generate dynamic dom elements on fly. You just need to initialize 
the domInjector() method for the container which holds the html part that needs to be dynamically created along with
the dynamic data set, 

## The initialization

If you have your own data set as array of objects, or array of arrays you can simple intilize like following-

	var data = [{ name : 'Ramesh', email: 'ramesh@xyx.com', status : 0, balance : 60000, date : '2016-5-10 12:10:10' },{name : 'Suresh', email: 'suresh@xyz.com', status : 1, balance : 20000, date : '2016-5-15 15:20:10'},{ name : 'Rajesh', email: 'rajesh@xyz.com', status : 1, balance : 5000, date : '2016-5-20 18:05:14' },{name : 'Mohan', email: 'mohan@xyz.com', status : 2, balance : 199000, date : '2016-5-21 22:30:00'}];
	$('#yourcontainer).domInjector(data);

Additonally if you have some server JSON data, then you can directly pass the request url as string in place of 
data argument, This library will itself launch the ajax request to that url, you can also pass the post data set as 
the 2nd argument.

	var postData = { category_id : xx  };
	/*OR*/ //var postData = $('#yourform').serialize(); 
	$('#yourcontainer).domInjector('http://yourwebsite.com/yourpagewhichreturnsjsonstring', postData);


## How To Put the Dynamic Data values automatically?

to put values from the data set you just need to put the keys inside a double square bracket [[key]]
and to write an expression with all your standard logics you need to put that inside double hash set ##your expression##

Example: 

<div id="yourcontainer" style="visibility: hidden;">
	<div style="float: left; width:19%;">[[name]]</div>
	<div style="float: left; width:19%;">[[email]]</div>
	<div style="float: left; width:19%;">##([[status]] == '1')?'Active':(([[status]] == '0')?'Not Verified':'Suspended')##</div>
	<div style="float: left; width:19%;">##showDate('[[date]]')##</div>
	<div style="float: left; width:19%;">Rs. [[balance]]/- ##(minBalance > [[balance]])?'Low Balance':''##</div>
	<div style="clear: both;"></div>
</div>



## Credit

Copyright 2016 Brij Patel.
