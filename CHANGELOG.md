Change Log
==========

All notable changes to this project will be documented in this file.

[0.5.2] - 2023-12-05
--------------------

* e8db05b -  Fix

[0.5.1] - 2022-07-05
--------------------

* 2c25e49 - Method String4::chars() can split an invalid string

[0.5] - 2022-07-04
------------------

* 7b40bd9 - Removed obsolete class String that only worked in PHP 5 (BC BREAK)
* ceeb1c0 - By default, String4::chars() returns array of String4

[0.4] - 2022-01-25
------------------

- Added methods
  * fixEncoding()
  * stripHtml()
  * isLower()
  * isUpper()
  * uncapitalize()

[0.3] - 2020-03-02
------------------
- String4::toSlug() improved, added options max_length and suffix

[0.2.1] - 2020-01-24
--------------------
### Fixed
- String4::gsub() fixed: in some cases string was recognized as callable

[0.2] - 2020-01-17
--------------------
- String4::capitalize()
- String4::gsub() accepts callback
- String4::camelize() and String4::underscore() support unicode

[0.1.1] - 2018-02-16
--------------------

### Fixed
- String4::toBoolean() fixed: it converts empty string to false

[0.1] - 2017-10-30
------------------

- First tagged version of the String4
