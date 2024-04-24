# isfirequest-js
IsfiRequest - The simple HTTP / RESTful requests library of JavaScript (XHR)

### Methods

- GET
- POST
- PUT
- PATCH
- DELETE
- Other
- JSON `(alias getJSON)`
- JSONP
- getScript

### Compatibility

- Firefox 4.0+
- Chrome 7+
- IE 9+
- Opera 11.60+
- Safari 5.1.4+

### Examples

Description :

	get|post|put|patch|delete|json(alias getJSON)(url, [data], [callback], [error], [options]);

GET :

```javascript
isfiReq.get("http://localhost/http-test/get.php?foo=Level1&bar=XHR&zh=中文", function(data) {
    //console.log(data, this);
}, function(method, url) {
    console.error("Custom Error", method, url, this.status, this.statusText);
});
```

POST :

```javascript
isfiReq.post("http://localhost/http-test/post.php?edfd=eedfd&dfsdf=ere", {
    a : 12,
    b : "bbbb",
    c : 123489
}, function(data) {
    console.log(data, this);
});
```

PUT :

```javascript
isfiReq.put("http://localhost/http-test/put.php?edfd=eedfd&dfsdf=ere", {
    a : 12,
    b : "bbbb",
    c : 123489
}, function(data) {
    console.log(data, this);
});
```

PATCH :

```javascript
isfiReq.patch("http://localhost/http-test/patch.php?edfd=eedfd&dfsdf=ere", {
    a : 12,
    b : "bbbb",
    c : 123489
}, function(data) {
    console.log(data, this);
});
```

DELETE :

```javascript
isfiReq.delete("http://localhost/http-test/delete.php?edfd=eedfd&dfsdf=ere", {
    a : 12,
    b : "bbbb",
    c : 123489
}, function(data) {
    console.log(data, this);
});
```

JSON (get json) :

```javascript
// Alias getJSON(), like jQuery
isfiReq.json("http://localhost/http-test/get-json.php?temp="+(new Date).getTime(), {
    test : 123
}, function(json) {
    console.log("get json =>", json);
});
```

JSONP :

    jsonp(url, [data], [callback], [callbackName]); // callbackName for query string name

```javascript
isfiReq.jsonp("http://192.168.1.2/http-test/jsonp.php?temp="+(new Date).getTime(), {
    test : 123
}, function(json) {
    console.log("jsonp =>", json);
}, "callback");
```

getScript :

```javascript
isfiReq.getScript("http://192.168.1.2/http-test/test.js", function() {
    test();
});
```

### Options

defaults :

```javascript
{
    debug         : false,
    async         : true,
    timeout       : 3000,
    method        : "GET",
    url           : "",
    data          : "",
    dataType      : "text",
    headers       : {},
    contentType   : "text/plain; charset=UTF-8",
    jsonp         : "callback",    // for query string
    xhrFields     : { //  like jQuery xhrFields options
        withCredentials : false
    },
    sendBefore    : function(xhr) {
        return xhr; // or return this, this == xhr
    },
    success       : function() {},
    error         : function(method, url) {},
    ontimeout     : function(method, url) {}
}
```

usage :

```javascript
isfiReq.request({
    url : "http://localhost/http-test/head.php",
    method : "HEAD",  // Custom http method
    headers : {},  // Custom http headers
    success : function(data) {
    	console.log(data, this, this.$request);
    }
});

isfiReq.get({
    url : "http://localhost/http-test/get.php?foo=bar",
    headers : {
    	"xxxxxxx" : "xxxxx"
    },
    success : function(data) {
    	console.log(data, this, this.$request);
    }
});

isfiReq.post({
    url : "http://localhost/http-test/post.php?foo=bar",
    data : {
    	id : 123,
    	title : "xxxxx"
    },
    headers : {
    	"xxxxxxx" : "xxxxx"
    },
    success : function(data) {
    	console.log(data, this, this.$request);
    }
});
