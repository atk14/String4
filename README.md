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

		echo $s->append(" My Dears"); // "Hello There! My Dears"
		echo $s->prepend("Hi! "); // "Hi! Hello There!"

    print_r($s->chars()); // ["H","e","l","l","o"," ","T","h","e","r","e","!"]
    echo $s->at(1); // "e"
    echo $s->substr(0,5); // "Hello"
		print_r($s->split(" ")); // ["Hello","There!"] 
		print_r($s->pregSplit('/\s+/')); // ["Hello","There!"] 

    var_dump($s->contains("Hello")); // true
    var_dump($s->containsOneOf("Hi","Ciao","Hey")); // falseq

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

		// chaining of methods
		$class_name = "CookieConsentsController";
		echo String4::ToObject($class_name)->gsub('/Controller$/','')->singularize()->underscore()->toString(); // "cookie_consent"

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
