<!---
layout: post
cover:  assets/images/build_url_shortener.png
title: Building a Simple URL Shortener With Just HTML and Javascript
navigation: True
tags: [Programming, Creating]
class: post-template
author: bauripalash
--->

# Building a Simple URL Shortener With Just HTML and Javascript

URL Shortener, you might have used one of them in your life such as [bit.ly](https://bit.ly), [goo.gl](https://goo.gl) and much more. They are useful for shortening long URLs so that you can easily share them with your friends, family or co-workers. 

You might be wondering how these things work? To understand how these things work, we need to take a closer look at an url shortener so we’ll be building a simple url shortener. With That Task, we’ll be learning some new things as well as understand how URL Shortener works.


Today, we'll be building a simple url shortener which does not need a database system to host yourself, instead, we'll use [jsonstore.io](https://jsonstore.io), I'll be assuming that you already know some basic HTML & Javascript. 

So without further talking, Let's Start Building. . .

## Start with HTML Part : 

we'll need only a text input box, a button, and a script tag to create our url shortener.

first create an HTML file called `index.html`, as there is only a need of two elements, a text input box, a button.

So Let's start adding our three main elements,

```html
<html>
    <body>
        <input type="url" id="urlinput">
        <button onclick="shorturl()">Short The URL</button>
        <script src="main.js"></script>
    </body>
</html>
```

As I shown in the above code, I've created a simple HTML file. Inside body tags, there're only three elements an `input`, a `button` and a `script`.

the first element is `input` where we well type/paste our long url, I gave it an id name `urlinput` so it would be easy to access it inside javascript.

Next element is a `button`, when we click this button our long url will be shortened as it has `onclick`function which will be executed when we click the button, inside the `shorturl()` function there will be commands necessary to shorten the url.

At the end we have a `script` called `main.js` where all our main javascript codes will be in, above mentioned `shorturl()` function will be also there.

So, for now, our HTML part is complete. so let's start writing some javascript


## Start writing some Javascript :

As we shown above, we'll need some javascript to create our url shortener.

**Step 0:** as I mentioned at first we'll be using **jsonstore.io** to store information about our long url, we will need a **jsonstore.io** **endpoint** url to store data, Visit [jsonstore.io](https://jsonstore.io), you'll see something like below

![Jsonstore Screenshot](https://palash.tk/assets/images/jsonstore_sshot.png)

Under the text _This Is Your Endpoint_ you can see a text box with long url such as,

```javascript
https://www.jsonstore.io/8ba4fd855086288421f770482e372ccb5a05d906269a34da5884f39eed0418a1
```

click the purple *COPY* button.

So Now, let's start writing some javascript . . .

create a javascript file called `main.js` and start following below steps

first, we must keep the copied link a variable

```javascript
var endpoint = "https://www.jsonstore.io/8ba4fd855086288421f770482e372ccb5a05d906269a34da5884f39eed0418a1";
```

then we need to generate some random string so that we can create a link between the short url and the long url.

> Assume, we have a random url `abcd`, our simple url shortener is hosted on <https://shortner.com> and we have shortened the url <https://google.com> with that random url, so whenever we go to <https://shortner.com/#abcd> we will be redirected to <https://google.com>

So, now well create a function called `getrandom()`

```javascript
function getrandom(){
    var random_string = Math.random().toString(32).substring(2, 5) + Math.random().toString(32).substring(2, 5);
    return random_string()
}
```

Don't worry, I'll help you understand the above code, 

first, we initiated a function called `getrandom` than we initialized a variable called `random_string` and gave it a value.

Math is a built-in javascript object which allows us to perform mathematical tasks on numbers. first we called the `random` function from `Math` , `Math.random()` returns a random number between 0 (inclusive),  and 1  (exclusive)

> You Can Learn More About `Math` object from [HERE](https://www.w3schools.com/js/js_math.asp) 

Then we transform the returned number to a string using `toString()` and we gave it an argument of 32 so that we get a proper string not a binary, hexadecimal or octal, 

Then we use `substring(2,5)` as well to slice the string and maintain the size of the string, then again we follow the same procedure to get another chunk of a random string and finally we add both chunks of the string using `+` 

and don't forget to add a `return` statement returning our random string.

> Remember, this is not the only way to generate random strings you can also use the technic mentioned below to achieve the goal

```

function getrandom() {
    var text = "";
    var possible = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";

    for (var i = 0; i < 5; i++)
        text += possible.charAt(Math.floor(Math.random() * possible.length));
    return text;
}

```


Now Return to `index.html` and add JQuery because it will be easy to achieve our goals with ease if we use JQuery.

add `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>` at the end of body tag but before the `main.js` script tag

now again return to `main.js`

let's Create a Function called `geturl` which will take the value from the input box verify it and return the value

```javascript

function geturl(){
    var url = document.getElementById("urlinput").value;
    var protocol_ok = url.startsWith("http://") || url.startsWith("https://") || url.startsWith("ftp://");
    if(!protocol_ok){
        newurl = "http://"+url;
        return newurl;
        }else{
            return url;
        }
}
```

in `geturl` function we first store the value of the input box in `url` variable. Then we check if url protocols are ok or not and if the protocol doesn't start with `http://` , `https://` or `ftp://` we add `http://` at the beginning of the url then return the url.

Now we will need another function to change the hash in the location bar, let's create

```javascript
function genhash(){
    if (window.location.hash == ""){
        window.location.hash = getrandom();
    }
}
```

At first, we check if the hash location is empty if it's empty we than add a random hash to the location bar.

> Example: if our url is <https://example.com/#abcd> then the value of `window.location.hash` will be `#abcd`


Next, we'll work on our main function `shorturl()` , so let's go...

```javascript
function shorturl(){
    var longurl = geturl();
    genhash();
    send_request(longurl);
}
```

At first we store the long url in `longurl` variable then we add a random hash to the location bar so that we can use the url as the short url , then we call the `send_request()` with an argument  `longurl` , in this function we send JSON request to **jsonstore** to store the long url with a link to short url , so now let's create the `send_request()` function.

```javascript

function send_request(url) {
    this.url = url;
    $.ajax({
        'url': endpoint + "/" + window.location.hash.substr(1),
        'type': 'POST',
        'data': JSON.stringify(this.url),
        'dataType': 'json',
        'contentType': 'application/json; charset=utf-8'
})
}
```

Here we use JQuery to send JSON request, we send the request to **endpoint+"/" + our random string hash from the location bar**
as an example, 

```javascript
https://www.jsonstore.io/8ba4fd855086288421f770482e372ccb5a05d906269a34da5884f39eed0418a1/abcd

```

so whenever we will send a get request to the above-mentioned url we'll get the long url as `data` 

**Important** : add the `send_request()` function before the `shorturl()` function ,  otherwise it will not work

> To Know More About JQuery's Ajax Function go [HERE](https://www.w3schools.com/jquery/ajax_ajax.asp)
To Know More About JSON, go [HERE](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON)

now we will the code to GET the long url linked to the short url entered in the address bar

```javascript
var hashh = window.location.hash.substr(1)

if (window.location.hash != "") {
    $.getJSON(endpoint + "/" + hashh, function (data) {
        data = data["result"];

        if (data != null) {
            window.location.href = data;
        }

    });
}
```

then the above-mentioned code will be executed whenever we put the short url in the address bar (eg. <https://shorturl.com/#abcd> )

at first, we store the hash value from the url to the `hashh` variable.

> Example: if our short url is https://shorted.com/#abcd , the value of hash will be **#abcd**

then we check if the hash location is empty or not, if not empty we send a get request to the address, `endpoint` + `hashh`

> Example : 
```javascript
https://www.jsonstore.io/8ba4fd855086288421f770482e372ccb5a05d906269a34da5884f39eed0418a1/abcd
```

and as usual, if everything is okay we will get the long url from the data which is a JSON array data, from that we extract the result with `data["result"]`.

> value of data will be similar to this `{"result":longurl,"ok":true}` , where long url is the url you shortened

Our URL Shortener is Almost Complete! Copy-Paste a long url in the input box then click **Short The URL** button! Copy The Link from Address Bar, it's your short url!

![Cheer Up Guys!](https://media1.tenor.com/images/00efa8c07f5a8b537b045544b6782e70/tenor.gif?itemid=4180838)

## Some Useful Tricks

We can add a function to automatically copy the short url when a user clicked the **Short The URL** button Using libraries like [SimpleCopy](https://github.com/kyle-rb/simplecopy), or [ClipboardJS](https://clipboardjs.com/) to copy the short url which is currently in the location bar.

if using SimpleCopy We can add `simplecopy(window.location.href);` at the end of `shorturl()` function copy the short url whenever use shortens a url

This Simple Url shortener relies on third-party libs such as **jsonstore** so it would not be a good idea to shorten some confidential long url with it.

You can host the Whole Project in Github/Gitlab pages and set up a simple CNAME, that's it your brand new personal url shortener is ready, you can use any static site hosting service to host your url shortener.

You Can Find the full source code of the Project in [GITHUB](https://github.com/bauripalash/simpleurlshortener)

---

That's it for today, That is my first technical guide article so I apologize for any mistakes, 

if you find any problems, mistakes, let me know the comments below 👇.

If You Liked My Work, Consider [Donating](https://palash.tk/donate) !

Peace!
