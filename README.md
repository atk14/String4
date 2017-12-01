String4
=======

String4 is a PHP class that provides methods for string manipulation. This package is part of the ATK14 Framework.

Basic usage
-----------

    $s = new String4("Hello There!");

    echo $s->lower(); // "hello there!"
    echo $s->upper(); // "HELLO THERE!"
    echo $s->length(); // 12
    print_r($s->chars()); // ["H","e","l","l","o"," ","T","h","e","r","e","!"]
    echo $s->replace("Hello","Hi"); // "Hi There!"
    echo $s->gsub('/[^a-z]/i','_');  // "Hello_There_"
    echo $s->at(1); // "e"
    echo $s->substr(0,5); // "Hello"
    var_dump($s->contains("Hello")); // true
    var_dump($s->containsOneOf("Hi","Ciao","Hey")); // false

Random string & password
------------------------

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

Use the Composer to install Files.

    cd path/to/your/project/
    composer require atk14/string4

Licence
-------

Files is free software distributed [under the terms of the MIT license](http://www.opensource.org/licenses/mit-license)
