# Vanilla JS Interview Prep:

# Soft Skills:
- I am a developer who is passionate about developing. I love developing in my spare time, I learn new skills and techniques in my spare time.
- Why do I need a job?
  - I need money, but it's a dream to be able to earn an income while doing something I actually enjoy!
  - I also need mentors, and a great team to work with an to guide me through best practices and to make me a better developer!

- Where do you see yourself in 10 years time?
  - I definitely want to stay a developer - I don't want to become a manager
  - Want to work my way up to the senior developer level

# Why Facebook?
-


# Any Questions?
- What will the internship involve?
- What is the technology stack? What should I learn?
- What will the hardest part of this job?
- Could you please give me feedback? What are the areas I should study and improve on?


# Topics of Interest
- Exploring **machine learning**
  - **Supervised learning** using decision trees
    - Tree of decisions and their consequences

  - **Naive Bayes** classification
    - Use cases:
      - To mark an email as spam or not spam
      - Classify a news article about technology, politics, or sports
      - Check a piece of text expressing positive emotions, or negative emotions
      - Used for face recognition software
      `P(A|B) = (P(B|A) P(A)) / P(B)`
        - P(A|B) is posterior probability, P(B|A) is likelihood, P(A) is class prior probability, and P(B) is predictor prior probability

  - **Gradient Descent**
    - Iterative optimisation algorithm for finding the minimum of a function



# Selectors
- ID: `document.getElementById('example');`
- Class: `document.querySelector('.example');`
  - multiple: `document.querySelectorAll('h2, div, span');`

# Strings:

#### `CharAt(index)`
  - Returns the character at the specified index

    ```JavaScript
    var str = "HELLO WORLD";
    var res = str.charAt(0);
    // H
    ```

#### `CharCodeAt(index)`
  - Returns the Unicode of the character at the specified index
    ```JavaScript
    var str = "HELLO WORLD";
    var n = str.charCodeAt(0);
    // 72
    ```

#### `Concat(string1, string2...stringX)`
  - Joins two or more strings, and returns a new joined string
    ```javascript
    var str1 = "Hello ";
    var str2 = "world!";
    var res = str1.concat(str2);
    // Hello world!
    ```

#### `EndsWith(searchValue, length)`
  - Checks whether a string ends with specified string/characters
    ```JavaScript
    var str = "Hello world, welcome to the universe.";
    var n = str.endsWith("universe.");
    // true
    ```

#### `FromCharCode(num1, num2...numX)`
  - Converts Unicode values to characters
    ```javascript
    var res = String.fromCharCode(65);
    // A
    ```

#### `Includes(searchValue, start)`
  - Checks whether a string contains the specified string/characters
    ```javascript
    var str = "Hello world, welcome to the universe.";
    var n = str.includes("world");
    // true
    ```

#### `IndexOf(searchValue, start)`
  - Returns the position of the first found occurrence of a specified value in a string
    ```javascript
    var str = "Hello world, welcome to the universe.";
    var n = str.indexOf("welcome");
    // 13
    ```

#### `LastIndexOf(searchValue, start)`
  - Returns the position of the last found occurrence of a specified value in a string
    ```javascript
    var str = "Hello planet earth, you are a great planet.";
    var n = str.lastIndexOf("planet");
    // 36
    ```

#### `LocaleCompare(compareString)`
  - Compares two strings in the current locale
    ```javascript
    var str1 = "ab";
    var str2 = "cd";
    var n = str1.localeCompare(str2);
    // -1 // str1 is sorted before str2
    ```

#### `Match(regexp)`
  - Searches a string for a match against a regular expression, and returns the matches
    ```javascript
    var str = "The rain in SPAIN stays mainly in the plain";
    var res = str.match(/ain/g);
    // ain,ain,ain
    ```

#### `Repeat(count)`
  - Returns a new string with a specified number of copies of an existing string
    ```javascript
    var str = "Hello world!";
    str.repeat(2);
    // Hello world!Hello world!
    ```

#### `Replace(searchValue, newValue)`
  - Searches a string for a specified value, or a regular expression, and returns a new string where the specified values are replaced
    ```javascript
    var str = "Visit Microsoft!";
    var res = str.replace("Microsoft", "W3Schools");
    // Visit W3Schools
    ```

#### `Search(searchValue)`
  - Searches a string for a specified value, or regular expression, and returns the index position of the match
    ```javascript
    var str = "Visit W3Schools!";
    var n = str.search("W3Schools");
    // 6
    ```

#### `Slice(start, end)`
  - Extracts a part of a string and returns a new string
    ```javascript
    var str = "Hello world!";
    var res = str.slice(1, 5);
    // ello
    ```

#### `Split(separator, limit)`
  - Splits a string into an array of substrings
    ```javascript
    var str = "How are you doing today?";
    var res = str.split(" ");
    // How,are,you,doing,today?
    ```

#### `StartsWith(searchValue, start)`
  - Checks whether a string begins with specified characters
    ```javascript
    var str = "Hello world, welcome to the universe.";
    var n = str.startsWith("Hello");
    // true
    ```

#### `Substr(start, length)`
  - Extracts the characters from a string, beginning at a specified start position, and through the specified number of characters
    ```javascript
    var str = "Hello world!";
    var res = str.substr(1, 4);
    // ello
    ```

#### `Substring(start, end)`
  - Extracts the characters from a string, between two specified indices
    ```javascript
    var str = "Hello world!";
    var res = str.substring(1, 4);
    // ell
    ```

#### `ToLocaleLowerCase()`
  - Converts a string to lowercase letters, according to the host's locale
    ```JavaScript
    var str = "Hello World!";
    var res = str.toLocaleLowerCase();
    // hello world!
    ```

#### `ToLocaleUpperCase()`
  - Converts a string to uppercase letters, according to the host's locale
    ```javascript
    var str = "Hello World!";
    var res = str.toLocaleUpperCase();
    // HELLO WORLD!
    ```

#### `ToLowerCase()`
  - Converts a string to lowercase letters
    ```javascript
    var str = "Hello World!";
    var res = str.toLowerCase();
    // hello world!
    ```

#### `ToString()`
  - Returns the value of a String object
    ```javascript
    var str = "Hello World!";
    var res = str.toString();
    // Hello World!
    ```

#### `ToUpperCase()`
  - Converts a string to uppercase letters
    ```javascript
    var str = "Hello World!";
    var res = str.toUpperCase();
    // HELLO WORLD!
    ```

#### `Trim()`
  - Removes whitespace from both ends of a string
    ```javascript
    var str = "       Hello World!        ";
    alert(str.trim());
    // Hello World!
    ```

#### `ValueOf()`
  - Returns the primitive value of a String Object
    ```javascript
    var str = "Hello World!";
    var res = str.valueOf();
    // Hello World!
    ```




# Arrays:
#### `Concat(array1, array2...arrayX)`
  - Joins two or more arrays, and returns a copy of the joined arrays
    ```javascript
    var hege = ["Cecilie", "Lone"];
    var stale = ["Emil", "Tobias", "Linus"];
    var children = hege.concat(stale);
    // Cecilie,Lone,Emil,Tobias,Linus
    ```

#### `CopyWithin(target, start, end)`
  - Copies array elements within the array, to and from specified positions
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.copyWithin(2, 0);
    // Banana,Orange,Banana,Orange
    ```

#### `Every(function(currentValue, index, arr), thisValue)`
  - Checks if every element in an array passes a test
    ```javascript
    var ages = [32, 33, 16, 40];

    function checkAdult(age) {
        return age >= 18;
    }

    function myFunction() {
        document.getElementById("demo").innerHTML = ages.every(checkAdult);
    }
    // false
    ```

#### `Fill(value, start, end)`
  - Fill the elements in an array with a static value
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.fill("Kiwi");
    // Kiwi,Kiwi,Kiwi,Kiwi
    ```

#### `Filter(function(currentValue, index, arr), thisValue)`
  - Creates a new array with every element in an array that passes a test
    ```JavaScript
    var ages = [32, 33, 16, 40];

    function checkAdult(age) {
        return age >= 18;
    }

    function myFunction() {
        document.getElementById("demo").innerHTML = ages.filter(checkAdult);
    }
    // 32,33,40
    ```

#### `Find(function(currentValue, index, arr), thisValue)`
  - Returns the value of the first element in an array that passes a test
    ```javascript
    var ages = [3, 10, 18, 20];

    function checkAdult(age) {
        return age >= 18;
    }

    function myFunction() {
        document.getElementById("demo").innerHTML = ages.find(checkAdult);
    }
    // 18
    ```

#### `FindIndex(function(currentValue, index, arr), thisValue)`
  - Returns the index of the first element in an array that passes a test
    ```javascript
    var ages = [3, 10, 18, 20];

    function checkAdult(age) {
        return age >= 18;
    }

    function myFunction() {
        document.getElementById("demo").innerHTML = ages.findIndex(checkAdult);
    }
    // 2
    ```

#### `ForEach(function(currentValue, index, arr), thisValue)`
  - Calls a function for each array element
    ```javascript
    <button onclick="numbers.forEach(myFunction)">Try it</button>
    <p id="demo"></p>

    <script>
    demoP = document.getElementById("demo");
    var numbers = [4, 9, 16, 25];

    function myFunction(item, index) {
        demoP.innerHTML = demoP.innerHTML + "index[" + index + "]: " + item + "<br>";
    }
    </script>
    /*
    index[0]: 4
    index[1]: 9
    index[2]: 16
    index[3]: 25
    */
    ```

#### `IndexOf(item, start)`
  - Search the array for an element and returns its position
    ```JavaScript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var a = fruits.indexOf("Apple");
    // 2
    ```

#### `isArray(obj)`
  - Checks if an object is an array
    ```JavaScript
    function myFunction() {
        var fruits = ["Banana", "Orange", "Apple", "Mango"];
        var x = document.getElementById("demo");
        x.innerHTML = Array.isArray(fruits);
    }
    // true
    ```

#### `Join(separator)`
  - Joins all elements of an array into a string
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var energy = fruits.join();
    // Banana,Orange,Apple,Mango
    ```

#### `LastIndexOf(item, start)`
  - Search the array for an element, starting at the end, and returns its position
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var a = fruits.lastIndexOf("Apple");
    // 2
    ```

#### `Map(function(currentValue, index, arr), thisValue)`
  - Creates a new array with the result of calling a function from each array element
    ```JavaScript
    var numbers = [4, 9, 16, 25];

    function myFunction() {
        x = document.getElementById("demo")
        x.innerHTML = numbers.map(Math.sqrt);
    }
    // 2,3,4,5
    ```

#### `Pop()`
  - Removes an element from the end of an array and returns removed item
    ```JavaScript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.pop();
    // Banana,Orange,Apple
    ```

#### `Push(item1, item2...itemX)`
  - Adds an element to the end of an array and returns new array length
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.push("Kiwi");
    // Banana,Orange,Apple,Mango,Kiwi
    ```

#### `Reduce(function(total, currentValue, currentIndex, arr), initialValue)`
  - Reduce the values of an array to a single value (going left-to-right)
    ```javascript
    var numbers = [65, 44, 12, 4];

    function getSum(total, num) {
        return total + num;
    }
    function myFunction(item) {
        document.getElementById("demo").innerHTML = numbers.reduce(getSum);
    }
    // 125
    ```

#### `ReduceRight(function(total, currentValue, currentIndex, arr), initialValue)`
  - Reduces the values of an array to a single value (going right-to-left)
    ```javascript
    var numbers = [65, 44, 12, 4];

    function getSum(total, num) {
        return total + num;
    }
    function myFunction(item) {
        document.getElementById("demo").innerHTML = numbers.reduceRight(getSum);
    }
    // 125
    ```

#### `Reverse()`
  - Reverses the order of the elements in an array
    ```JavaScript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.reverse();
    // Mango,Apple,Orange,Banana
    ```

#### `Shift()`
  - Removes an element from the beginning of an array and returns removed item
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.shift();
    // Orange,Apple,Mango
    ```

#### `Slice(start, end)`
  - Selects a part of an array, and returns the new array
    ```javascript
    var fruits = ["Banana", "Orange", "Lemon", "Apple", "Mango"];
    var citrus = fruits.slice(1, 3);
    // Orange, Lemon
    ```

#### `Some(function(currentValue, index, arr), thisValue)`
  - Checks if any of the elements in an array passes a test
    ```javascript
    var ages = [3, 10, 18, 20];

    function checkAdult(age) {
        return age >= 18;
    }

    function myFunction() {
        document.getElementById("demo").innerHTML = ages.some(checkAdult);
    }
    // true
    ```

#### `Sort(compareFunction)`
  - Sorts the elements of an array
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.sort();
    // Apple,Banana,Mango,Orange
    ```

#### `Splice(index, howMany, item1...itemX)`
  - Adds/Removes elements from an array
    ```JavaScript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.splice(2, 0, "Lemon", "Kiwi");
    // Banana,Orange,Lemon,Kiwi,Apple,Mango
    ```

#### `ToString()`
  - Converts an array to a string, and returns the result
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.toString();
    // Banana,Orange,Apple,Mango
    ```

#### `Unshift(item1, item2...itemX)`
  - Adds an element to the beginning of an array and returns new array length
    ```JavaScript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    fruits.unshift("Lemon","Pineapple");
    // Lemon,Pineapple,Banana,Orange,Apple,Mango
    ```

#### `ValueOf()`
  - Returns the primitive value of an array
    ```javascript
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var v = fruits.valueOf();
    // Banana,Orange,Apple,Mango
    ```







# Objects: (`Object.[method]`)
#### `Assign(target, ...sources)`
  - Copies the values of all enumerable own properties from one or more source objects to a target object
    ```JavaScript
    const object1 = {
      a: 1,
      b: 2,
      c: 3
    };

    const object2 = Object.assign({}, object1);

    console.log(object2.c);
    // expected output: 3
    ```

#### `Create(prototype[anyProperties])`
  - Creates a new object with the specified prototype object and properties
    ```JavaScript
    function Shape() {
      this.name = 'Shape 1';
    }

    function Rectangle() {
      Shape.call(this);
    }

    Rectangle.prototype = Object.create(Shape.prototype);
    const rect = new Rectangle();

    console.log(rect.name);
    // expected output: "Shape 1"
    ```

#### `DefineProperty(obj, prop, descriptor)`
  - Adds the named property described by a given descriptor to an object
    ```javascript
    const object1 = {};

    Object.defineProperty(object1, 'property1', {
      value: 42,
      writable: false
    });

    object1.property1 = 77;
    // throws an error in strict mode

    console.log(object1.property1);
    // expected output: 42
    ```

#### `DefineProperties(obj, props)`
  - Adds the named properties described by the given descriptors to an object
    ```javascript
    const object1 = {};

    Object.defineProperties(object1, {
      property1: {
        value: 42,
        writable: true
      },
      property2: {}
    });

    console.log(object1.property1);
    // expected output: 42
    ```

#### `Entries(obj)`
  - Returns an array of a given object's own enumerable property [key, value] pairs
    ```javascript
    const object1 = { foo: 'bar', baz: 42 };
    console.log(Object.entries(object1)[1]);
    // expected output: Array ["baz", 42]

    const object2 = { 0: 'a', 1: 'b', 2: 'c' };
    console.log(Object.entries(object2)[2]);
    // expected output: Array ["2", "c"]

    const object3 = { 100: 'a', 2: 'b', 7: 'c' };
    console.log(Object.entries(object3)[0]);
    // expected output: Array ["2", "b"]
    ```

#### `Freeze(obj)`
  - Freezes and object: other code can't delete or change any properties
    ```javascript
    const object1 = {
      property1: 42
    };

    const object2 = Object.freeze(object1);

    object2.property1 = 33;
    // Throws an error in strict mode

    console.log(object2.property1);
    // expected output: 42
    ```

#### `GetOwnPropertyDescriptor(obj, prop)`
  - Returns a property descriptor for a named property of an object
    ```JavaScript
    const object1 = {
      property1: 42
    }

    const descriptor1 = Object.getOwnPropertyDescriptor(object1, 'property1');

    console.log(descriptor1.configurable);
    // expected output: true

    console.log(descriptor1.value);
    // expected output: 42
    ```

#### `GetOwnPropertyDescriptors(obj)`
  - Returns an object containing all property descriptors for an object
    ```javascript
    const object1 = {
      property1: 42
    };

    const descriptors1 = Object.getOwnPropertyDescriptors(object1);

    console.log(descriptors1.property1.writable);
    // expected output: true

    console.log(descriptors1.property1.value);
    // expected output: 42
    ```

#### `GetOwnPropertyNames(obj)`
  - Returns an array containing the names of all the given object's own properties
    ```JavaScript
    const object1 = {
      a: 1,
      b: 2,
      c: 3
    };

    console.log(Object.getOwnPropertyNames(object1));
    // expected output: Array ["a", "b", "c"]
    ```

#### `GetOwnPropertySymbols(obj)`
  - Returns an array of all symbol properties found directly upon a given object
    ```javascript
    const object1 = {};
    const a = Symbol('a');
    const b = Symbol.for('b');

    object1[a] = 'localSymbol';
    object1[b] = 'globalSymbol';

    const objectSymbols = Object.getOwnPropertySymbols(object1);

    console.log(objectSymbols.length);
    // expected output: 2
    ```

#### `GetPrototypeOf(obj)`
  - Returns the prototype of the specified object
    ```JavaScript
    const prototype1 = {};
    const object1 = Object.create(prototype1);

    console.log(Object.getPrototypeOf(object1) === prototype1);
    // expected output: true
    ```

#### `Is(value1, value2)`
  - Compares if two values are the same value. Equates all NaN values (which differs from == and ===)
    ```JavaScript
    Object.is('foo', 'foo');     // true
    Object.is(window, window);   // true

    Object.is('foo', 'bar');     // false
    Object.is([], []);           // false

    var test = { a: 1 };
    Object.is(test, test);       // true

    Object.is(null, null);       // true

    // Special Cases
    Object.is(0, -0);            // false
    Object.is(-0, -0);           // true
    Object.is(NaN, 0/0);         // true
    ```

#### `IsExtensible(obj)`
  - Determines if extending of an object is allowed
    ```JavaScript
    const object1 = {};

    console.log(Object.isExtensible(object1));
    // expected output: true

    Object.preventExtensions(object1);

    console.log(Object.isExtensible(object1));
    // expected output: false
    ```

#### `IsFrozen(obj)`
  - Determines if an object is frozen
    ```javascript
    const object1 = {
      property1: 42
    };

    console.log(Object.isFrozen(object1));
    // expected output: false

    Object.freeze(object1);

    console.log(Object.isFrozen(object1));
    // expected output: true
    ```

#### `IsSealed(obj)`
  - Determines if an object is sealed
    ```JavaScript
    const object1 = {
      property1: 42
    };

    console.log(Object.isSealed(object1));
    // expected output: false

    Object.seal(object1);

    console.log(Object.isSealed(object1));
    // expected output: true
    ```

#### `Keys(obj)`
  - Returns an array containing the names of all of the object's own properties
    ```JavaScript
    // simple array
    var arr = ['a', 'b', 'c'];
    console.log(Object.keys(arr)); // console: ['0', '1', '2']

    // array like object
    var obj = { 0: 'a', 1: 'b', 2: 'c' };
    console.log(Object.keys(obj)); // console: ['0', '1', '2']

    // array like object with random key ordering
    var anObj = { 100: 'a', 2: 'b', 7: 'c' };
    console.log(Object.keys(anObj)); // console: ['2', '7', '100']

    // getFoo is a property which isn't enumerable
    var myObj = Object.create({}, {
      getFoo: {
        value: function () { return this.foo; }
      }
    });
    myObj.foo = 1;
    console.log(Object.keys(myObj)); // console: ['foo']
    ```

#### `PreventExtensions(obj)`
  - Prevents any extensions of an object
    ```javascript
    const object1 = {};

    Object.preventExtensions(object1);

    try {
      Object.defineProperty(object1, 'property1', {
        value: 42
      });
    } catch (e) {
      console.log(e);
      // Expected output: TypeError: Cannot define property property1, object is not extensible
    }
    ```

#### `Seal(obj)`
  - Prevents other code from deleting properties of an object
    ```JavaScript
    const object1 = {
      property1: 42
    };

    Object.seal(object1);
    object1.property1 = 33;
    console.log(object1.property1);
    // expected output: 33

    delete object1.property1; // cannot delete when sealed
    console.log(object1.property1);
    // expected output: 33
    ```

#### `SetPrototypeOf(obj, prototype)`
  - Sets the prototype
    ```javascript
    var dict = Object.setPrototypeOf({}, null);
    ```

#### `Values(obj)`
  - Returns an array of all of the objects own values
    ```JavaScript
    const object1 = {
      a: 'somestring',
      b: 42,
      c: false
    };

    console.log(Object.values(object1));
    // expected output: Array ["somestring", 42, false]
    ```


---


# Process from entering a URL to it appearing in your browser
1. You type the URL into the browser
2. Browser checks the cache for a DNS record to fin the corresponding IP address for the URL
    - DNS(Domain Name System) is a database that maintains the name of the website (URL) and the particular IP address it links to
    - Offers human-friendly navigation
  - First, checks browser cache
  - Second, checks the OS cache
  - Third, checks the router cache
  - Fourth, checks the ISP cache
3. If the URL is not in the cache, the ISP's DNS server initiates a DNS query to find the IP address
  - Requests are sent using small data packets with content of the request and the IP address it is destined for
  - If packets are lost, you get a request failed error
  - Otherwise, they will reach the correct DNS server, grab the correct IP address and come back to the browser
4. Browser initiates a TCP connection with the server
  - Once it receives the correct IP address, the browser builds a connection with that server.
  - TCP connection is established via the TCP/IP three-way handshake
    - Client sends SYN packet (start flag) to server asking if it is open for new connections
    - If the server has open ports that can accept/initiate new connections, it responds with an ACKnowledgement of the SYN packet using a SYN/ACK packet (ACK means it is expecting data)
    - The client receives the SYN/ACK packet and acknowledges it by sending an ACK packets
    - TCP connection is established!
5. Browser sends an HTTP request to the web server
  - Browser sends GET request (if submitting a form, it could be a POST request)
  - Request also contains additional information:
    - browser identification (User-Agent header)
    - types of requests that it will accept (Accept-header)
    - connection headers asking to keep the TCP connection alive for additional requests

6. Server handles the request
  - Web server receives request and passes it to a request handler to read and generate a response (JSON, XML, HTML)

7. Server sends back an HTTP response
  - Server response contains:
    - the web page you requested
    - the status code
      - 1xx indicates informational message only
      - 2xx indicates success of some kind
      - 3xx redirects the client to another URL
      - 4xx indicates an error on the client's part
      - 5xx indicates an error on the server's part
    - compression type (Content-Encoding)
    - how to cache the page (Cache-Control)
    - any cookies to set
    - privacy information
    - etc.

8. Browser displays the HTML content (for HTML responses)
  - First renders bare bone HTML skeleton
  - Then checks HTML tags and sends out GET requests for additional elements on the page (images, CSS stylesheets, JavaScript files etc)
  - Are then cached by the browser so it doesn't have to fetch again


## HTTP/S Protocols
Request/Response protocol between client and server

#### Difference between `GET` and `POST`
- GET:
  - Request is in the header of the message sent
- POST:
  - Request is in the body of the message sent

#### URLs (Uniform Resource Locators)
```
http://www.domain.com:1234/path/to/resource?a=b&x=y
```
Structure:
  - Protocol `http`
  - Host `www.domain.com`
  - Port `:1234`
  - Resource Path `/path/to/resource`
  - Query `?a=b&x=y`

## TCP
- requires three-way handshake


## UDP
- sends continuous stream


# CORS
- Policy that protects against other origins from sharing resources with you or other websites hitting yours


# AJAX
1. An event occurs in a web page (the page is loaded, a button is clicked)
2. An `XMLHttpRequest` object is created by JavaScript
3. The `XMLHttpRequest` object sends a request to a server
4. The server processes the request
5. The server sends back a response back to the client
6. The response is ready by JavaScript
7. Proper action (like page update) is performed by JavaScript

```javascript
function loadDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if(this.readyState == 4 && this.status == 200) {
      document.getElementById('demo').innerHTML = "Loaded!";
    }
  };

  xhttp.open("GET", "fileOnServer.txt", true);
  xhttp.send();
}

// can be instigated by:
// <button type="button" onclick="loadDoc()">Load New Content</button>
```



---



# Interview Questions:

## What is JavaScript?
  - A scripting language
  - Object-based, lightweight and cross-platform
  - Widely used for client-side validation, but Node.js allows it to handle back-end handling of servers


## What is the BOM?
  - Browser Object Model
  - Provides interaction with the browser
  - The default object of browser is the `window` object


## What is the DOM?
  - Document Object Model
  - Represents the html document and can be accessed and edited


## What is the History object?
  - Used to switch to browsing history
  - Three methods:
    - `history.back();`
    - `history.forward();`
    - `history.go(number);` - positive for forward, negative for backward


## What are the JavaScript data types?
  - Two data types:
    - **Primitive** data types
      - *Number*, *String*, *Boolean*, *Symbol* (ES6)
    - **Composite** data types (can be constructed using primitive)
      - *Object*, *Array*
    - **Special** data types
      - *Undefined*, *Null*


## How to write html code dynamically using JavaScript?
  - innerHTML property used
    ```JavaScript
    document.getElementById('mylocation').innerHTML="<h2>This is new</h2>";
    ```

## How do you create an object?
  - By object literal
    ```javascript
    var obj = {id: 102, name: "test", hobby: "basketball"};
    ```
  - By creating an instance of an Object from a class
    ```javascript
    class Obj {constructor(a, b) { this.a = a; this.b = b;}}
    var o = new Obj();
    ```
  - By Object constructor
    ```javascript
    var Obj = function(a,b) { this.a = a; this.b = b}

    var o = new Obj();
    ```

## Explain Event Delegation
  - JavaScript as it relates to the DOM.
  - If you attach an event listener on a single DOM element, that event listener fires on all child elements on that element as well.
  - Event Bubbling


## Describe Event Bubbling/Propogation
  - Inverse of Event Delegation
  - Events on an element will 'bubble up' and also fire on all parents


## What's the difference between "target" and "currentTarget"?
  - "currentTarget" is the element with the listener attached, "target" is the actual element that triggered it


## Explain why the following doesn't work as an IIFE:
	```javascript
  function foo() {
    // to do here //
	}();
  ```
  - IIFE: Immediately invoked function expression
  - Cannot immediately invoke definitions -> need to assign to variable and define beforehand
  - Can convert to IIFE by (function foo(){ })(); wrapping parentheses around
  - Why would you use one?
    - To control variable scope


## Explain the difference between using function foo() and var foo = function()
  - Function as expressions vs statements


## Why is it, in general, a good idea to leave the global scope of a website as-is and never touch it?
  - Can't predict the future
  - Reduce collision (naming)
  - Maintain independence
  - Easier to write your own code (use own naming conventions)


## Explain 'hoisting'
  - All variables (var) are declared at the top of any given function scope whether you like it or not (includes function statements)
  - Solved by const and let
    - Not Hoisted
    - Scoped within the block they are in
    - Gives you more control
    - const is immutable, whereas let is


## What's the difference between a variable that is null, undefined or undeclared?
  - undeclared e.g.. const bar = foo + 1;
    - You forgot something somewhere - something's gone wrong
  - undefined
    - You have declared a variable but it hasn't been assigned or instantiated yet
    - e.g. uninstantiated variables, attributes of objects that aren't defined, index values of arrays that don't exist, or functions that don't return anything
    - Falsy
    - With const, you must assign a value when you declare it!
  - null e.g. const queue = null;
    - is a value, but is interpreted as having the value of 'nothing'


## How would you go about checking for any of these states?
  - undeclared
    - usually finds you, except when assigning a value (automatically assigns to global scope if undeclared)
  - undefined
    - using typeof a declared variable returns 'undefined' as a string
    - using typeof an undeclared variable also returns 'undefined' as a string
    - PREFERRED check for undefined: if foo === undefined - results in true boolean
  - null
    - typeof null returns an object?! -> Bug?!
    - PREFERRED check for null with ===


## What is the difference between '==' and '==='?
  - triple equals => check for equality and type
  - double equals => check for equality alone


## What is the event loop?
- In order to simulate multi-threaded capabilities, asynchronous calls get added to a queue, which the event loop keeps going through and executing whenever the next item is enqueued


## Object Equality
- Objects and arrays are compared by their reference, not value
- `Object.getOwnPropertyNames(obj)` returns an array of property keys that we can iterate through and test against


## Extend Core Object Functionality
- Extending prototypes


## Bind
- binds the `this` keyword to a function or scope


## Explain Arguments
- Arguments object is a local variable available within all non-arrow functions
- Similar to an array, but NOT an array (doesn't have `length` method)


## Closures and Currying
- They are created whenever a variable that is defined outside the current scope is accessed from within some inner scope
- How to use in setTimout()?
  - use .bind() or set `this` to `var that`
  - use ES6 arrow functions

- Currying: partial invocation of a function
  - First few arguments of a function is pre-processed and a function is returned (creating a Closure that returns a function!)
  - Returning function can add more arguments to the curried function
  ```javascript
  function addBase(base){
    return function(num){
      return base + num;
    }
  }

  var addTen = addBase(10);
  addTen(5); //15
  addTen(80); //90
  addTen(-5); //5
  ```


## Memoization
- Dynamic programming technique to improve the asymptotic runtime of a function or algorithm
- For example:
  - Can be used to cache previously obtained data in a recursive function, for example


## Animation
```javascript
function moveLeft(elem, distance) {
  var left = 0;

  function frame() {
    left++;
    elem.style.left = left + 'px';

    if (left == distance)
      clearInterval(timeId)
  }

  var timeId = setInterval(frame, 10); // draw every 10ms
}
```


## How to access query string in a browser's URL?
  - window.location.search


## Web-based questions
- Explain HTTP Negotiation Steps


## The `this` keyword
- Refers to the current context
- By default, refers to the **window** object
- Only assigns to instantiated functions (not anonymous functions by default)


## Closures
- They are created whenever a variable that is defined outside the current scope is accessed from within some inner scope


## What is Debounce?
- used to defer function callbacks from event listeners by a certain amount of time
- Eg. if user is typing, rather than firing multiple times after each keyup, fire once after 500ms


## Explain prototypes
- Used to promote OOP traits in JS
- Allows inheritance


## Difference between `==` and `===`?
- Equality vs Equality and Type


## Benefits of using `use strict`
- Avoid certain errors
  - eg. throws error if global var created
  - eliminates `this` coersion
  - prevents duplicate names or values


## What is NaN?
- Not a number
- test for using `isNaN()`
  - because typeof NaN is String and `NaN === NaN` is false?!


## What is a Promise?
- A returning function or callback that will be **resolved**, but not necessarily immediately
- Avoids callback hell (having to for callback functions to return before running nested parent callback)
  - calls callbacks when data is available (potentially after an ajax call) using the `then` method
  - ES7 introduced the `await` function
