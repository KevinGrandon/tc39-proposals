## Proposal: Addition of string padding functions.

```
String.prototype.lpad(minLength, fillStr = ' ')
String.prototype.rpad(minLength, fillStr = ' ')
```

**Rationale:**

Without a reasonable way to pad a string using native methods, working with Javascript strings today is more painful than it should be. Without these functions, the language feels incomplete, and is a paper cut to what could be a very polished experience.

Due to common use, string padding functions exist in a majority of websites and frameworks. For example, nearly every app in FirefoxOS had implemented a left pad function, because they all needed some generic string padding operation.

It is highly probable that the majority of current string padding implementations are inefficient. Bringing this into the platform will improve performance of the web, and developer productivity as they no longer have to implement these common functions. 


**Arguments:**

minLength: (Integer, Optional) The total minimum length of the return string. The new string will be constructed as the original string, plus any additional padding characters required to fill the minimum length.

fillStr:  (String, Optional, Default=' ') The string to pad the original string with. The string may be truncated if the string length is not evenly divisible by the remaining characters to fill. For internationalization purposes, a string is used here to ensure compatibility with 32-bit unicode characters.


**Return:**

Returns a new padded string, which meets the minimum length specified.


###lpad specification###

1. Let *O* be CheckObjectCoercible(**this** value).

2. Let *S* be ToString(O).

3. ReturnIfAbrupt(S).

4. Let *intMinLength* be ToInteger(minLength).

5. ReturnIfAbrupt(intMinLength).

4. If *intMinLength* is **undefined**, return *S*.

5. Let *fillLen* be the number of characters in *S* minus *intMinLength*.

6. If *fillLen* < 0, then throw a **RangeError** exception.

7. If *fillLen* is +∞, then throw a **RangeError** exception.

8. Let *sFillStr* be the string represented by fillStr.

9. If *sFillStr* is **undefined**, let *sFillStr* be a space character.

10. Let *sFillVal* be a *String* made of *sFillStr*, repeated until *fillLen* is met.

11. Return a string made from *sFillVal*, followed by *S*.


###rpad specification###

1. Let *O* be CheckObjectCoercible(**this** value).

2. Let *S* be ToString(O).

3. ReturnIfAbrupt(S).

4. Let *intMinLength* be ToInteger(minLength).

5. ReturnIfAbrupt(intMinLength).

4. If *intMinLength* is **undefined**, return *S*.

5. Let *fillLen* be the number of characters in *S* minus *intMinLength*.

6. If *fillLen* < 0, then throw a **RangeError** exception.

7. If *fillLen* is +∞, then throw a **RangeError** exception.

8. Let *sFillStr* be the string represented by fillStr.

9. If *sFillStr* is **undefined**, let *sFillStr* be a space character.

10. Let *sFillVal* be a *String* made of *sFillStr*, repeated until *fillLen* is met.

11. Return a String made from *S*, followed by *sFillVal*.


**Naming convention:**

Currently named lpad and rpad for berevity and readability, but we are willing to consider alternatives. Potential alternatives include ljust and rjust,  or the more verbose padLeft and padRight. See the next precedents section.


**Precedents:**

Python

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')

Ruby

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')
