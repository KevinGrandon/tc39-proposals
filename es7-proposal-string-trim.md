## Proposal: Addition of string trim functions.

```
String.prototype.ltrim()
String.prototype.rtrim()
```

**Rationale:**

Having standardized a String trim method, as well as currently standardizing left and right String padding methods, adding a method to trim the left and right side of strings would be a small win for Javascript.


**Arguments:**

None. Like the trim function, no arguments are needed for ltrim and rtrim. Currently only whitespace trimming is supported, but we could also trim other characters from strings as well.


**Return:**

Returns a trimmed string.


**Naming convention:**

Currently named ltrim and rtrim for berevity and readability, but we are willing to consider alternatives. Potential alternatives include trimleft and trimRight. See the next precedents section.


**Precedents:**

Python

* lstrip(chars)
* rstrip(chars)

Ruby

* lstrip
* rstrip
