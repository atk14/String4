String4
=======

[![Build Status](https://app.travis-ci.com/atk14/String4.svg?token=Kc7UxgK5oqFG8sZAhCzg&branch=master)](https://app.travis-ci.com/atk14/String4)

String4 is a PHP class that provides methods for string manipulation.

Basic usage
-----------

    $s = new String4("Hello There!");
    echo $s->lower(); // "hello there!"
    echo $s->upper(); // "HELLO THERE!"
    echo $s->length(); // 12
    echo $s->replace("Hello","Hi"); // "Hi There!"
    echo $s->gsub('/[^a-z]/i','_');  // "Hello_There_"
    echo $s->toSlug()(); // "hello-there"
    echo $s->truncate(6); // "Hel..."
    echo $s->toSlug(); // "hello-there"
    echo $s->toSlug(8); // limiting max length - "hello-th"

    echo $s->append(" My Dears"); // "Hello There! My Dears"
    echo $s->prepend("Hi! "); // "Hi! Hello There!"

    print_r($s->chars()); // ["H","e","l","l","o"," ","T","h","e","r","e","!"]
    echo $s->at(1); // "e"
    echo $s->substr(0,5); // "Hello"
    print_r($s->split(" ")); // ["Hello","There!"] 
    print_r($s->pregSplit('/\s+/')); // ["Hello","There!"] 

    var_dump($s->contains("Hello")); // true
    var_dump($s->containsOneOf("Hi","Ciao","Hey")); // false

    // Trimming string
    $s = $s->trim();
    // or
    $s = $s->trim(true); // trim also other control and non-displayable characters

    // Converting string to a boolean value
    String4::ToObject("Y")->toBoolean(); // true
    String4::ToObject("on")->toBoolean(); // true
    String4::ToObject("True")->toBoolean(); // true
    String4::ToObject("NO")->toBoolean(); // false
    String4::ToObject("off")->toBoolean(); // false
    String4::ToObject("0")->toBoolean(); // false
    // etc

    // Fixing document encoding
    $s = $s->fixEncoding();
    // or
    $s = $s->fixEncoding(["replacement" => "?"]); // setting a replacement for an invalid char

    // Intelligent HTML tag removal
    $html = "<h1>Welcome at our <em>web</em><small>site</small>!</h1><p>We are here to help you.<br>Write us.</p>";
    $s = new String4($html);
    echo $s->stripHtml(); // Welcome at our website! We are here to help you. Write us.

    // Instantiation by a static method
    $s = String4::ToObject("Hello There!");

    // Singularize & pluralize
    $s = new String4("Happy people");
    echo $s->singularize(); // "Happy person"
    $s = new String4("Sad man");
    echo $s->pluralize(); // "Sad men"

    // Chaining of methods
    $class_name = "CookieConsentsController";
    echo String4::ToObject($class_name)->gsub('/Controller$/','')->singularize()->underscore()->toString(); // "cookie_consent"

    // Removing empty lines
    $s = $s->removeEmptyLines();
    // or with options
    $s = $s->removeEmptyLines([
      "max_empty_lines" => 2, // default 0
      "trim_empty_lines" => false, // default true
    ]);

    // Filtering text document
    // (e.g. removing empty lines from a document)
    echo String4::ToObject($text_document)->eachLineFilter(
      function($line){
        return $line->trim()->length()>0;
      }
    )->toString();

    // Applying function on each line
    // (e.g. trimming each line)
    echo String4::ToObject($text_document)->eachLineMap(
      function($line){
        return $line->trim();
      }
    )->toString();

Random strings & passwords
--------------------------

Method String4::RandomString() generates string of the given length composed of random characters taken from the set [a-zA-Z0-9].

    echo String4::RandomString(10); // "7VGlhe3EzR"

    // extra characters can also be specified
    echo String4::RandomString(["length" => 15, "extra_chars" => "#!&@"]); // "@vIxpVo!qD4A#n5"

Method String4::RandomPassword() generates random string from a smaller set of characters than String4::RandomString().
Some characters which can cause a confusion are excluded, e.g. "1","l","O","0".

    echo String4::RandomPassword(12); // 68ynedeSA634

String4::RandomPassword() can be also used as a voucher codes generator:

    echo String4::RandomPassword(10)->upper(); // EVUH923244

Installation
------------

Use the Composer to install String4.

    cd path/to/your/project/
    composer require atk14/string4

Licence
-------

String4 is free software distributed [under the terms of the MIT license](http://www.opensource.org/licenses/mit-license)

[//]: # ( vim: set ts=2 et: )
