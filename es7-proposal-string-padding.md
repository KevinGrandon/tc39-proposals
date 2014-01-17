## Proposal: Addition of string padding functions.

```
String.prototype.lpad(minLength, fillChar = ' ')
String.prototype.rpad(minLength, fillChar = ' ')
```

**Arguments:**

minLength: (Integer, Optional) The total minimum length of the return string. The new string will be constructed as the original string, plus any additional padding characters required to fill the minimum length.

fillChar:  (String, Optional, Default=' ') The character to pad the original string with.


**Return:**

Returns a new padded string, which meets the minimum length specified.


**Rationale:**

These are two functions that exist in a majority of websites and frameworks. For example, nearly every app in FirefoxOS had implemented a left pad function, because they all needed some generic string padding operation

It is highly probable that the majority of current String padding implementations are inefficient. Bringing this into the platform will improve performance of the web, and developer productivity as they no longer have to implement these common functions. 


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

8. Let *chFillChar* be the character represented by fillChar.

9. If *chFillChar* is **undefined**, let *chFillChar* be a space character.

10. Return a String containing *fillLen* repitions of *chFillChar*, followed by *S*.</li>


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

8. Let *chFillChar* be the character represented by fillChar.

9. If *chFillChar* is **undefined**, let *chFillChar* be a space character.

10. Return a String containing *S*, followed by *fillLen* repitions of *chFillChar*.</li>


**Naming convention:**

Currently named lpad and rpad for berevity and readability, but we are willing to consider alternatives. Potential alternatives include ljust and rjust,  or the more verbose padLeft and padRight. See the next precedents section.

**Precedents:**

Python

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')

Ruby

* ljust(integer, fillChar=' ')
* rjust(integer, fillChar=' ')
