## Proposal: Addition of string padding functions.

```
String.prototype.lpad(minLength, fillChar)
String.prototype.rpad(minLength, fillChar)
```

**Arguments:**

minLength: (Integer, Optional) The total minimum length of the return string. The new string will be constructed as the original string, plus any additional padding characters required to fill the minimum length.

fillChar:  (String, Optional, Default=' ') The character to pad the original string with.


**Return:**

Returns a new padded string, which meets the minimum length specified.


**Rationale:**

These are two functions that exist in a majority of websites and frameworks. For example, nearly every app in FirefoxOS had implemented a left pad function, because they all needed some generic string padding operation

It is highly probable that the majority of current String padding implementations are inefficient. Bringing this into the platform will improve performance of the web, and developer productivity as they no longer have to implement these common functions. 


**Naming convention:**

Currently named lpad and rpad for berevity and readability, but we are willing to consider alternatives. Potential alternatives include ljust and rjust,  or the more verbose padLeft and padRight. See the next precedents section.

**Precedents:**

Python

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')

Ruby

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')
