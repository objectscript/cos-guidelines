# cos-guidelines
This is the first approximation of COS guidelines we use for github.com/intersystems-ru projects. There are mandatory and recommended parts.

We do not plan to be very restrictive, but want be rather flexible enough and allow any *reasonable* style.
Here is the general advice: use common sense and try to *be consistent* wherever you write code. 
If there is some style already established in the class or utility being modified then we recommend
to continue use that same style, than introducing yet another one, which may be more recommended 
but which will be introducing some unnecessary inconsistency.

## Mandatory part

* Only "modern" syntax permitted, dotted syntax is not generally allowed (with few exceptions);
* No short name for statements keywords or built-in functions allowed - use fully expanded names;
* Comment your code appropriately, use English in comments to make your code easy to understand by your international collegues. Same English-based rule applies to global, local, and type names.
 
## Recommended part
* We recommend to use fully expanded keyword or function name in lower case or capitalized. Whatever you'll select should be consistent across class or utility, i.e.
```
If (expression) {
  Do ##class(Sample).%New(initexpresion)
  For i=1:1:10 {
    Write something, $ZVersion, !
  }
}
```
  or

```
 if (expression) {
   do ##class(Sample).%New(initexpresion)
   for i=1:1:10 {
     write something, $zversion, !
   }
 }
```
* Use the reasonable name convention consistently across whole hierarchy. We recommend to use CamelCase for classes, methods and properties (e.g. `Sample.Person`, `OpenFile`, `LastIndex`, etc.), but smallCamelCase for local variables (e.g. `startDate`, `endDate`), but please be consistent and use local schema if it's different than current recommendation.
* We recommend to use `#dim` statement for declaration of local variables types, e.g.
```
  #dim array as %ArrayOfDataTypes = ##class(%ArrayOfDataTypes).%New()
  do array.SetAt(id, "id")
  #dim status As %Status = $$$OK
```
 This will help editor to provide better auto-complete, and eventually will be used by static checker for type informantion extraction.
* Please indent blocks reasonably. We recommend to use 8, 4 or 2 spaces indentations. Pick your level, and apply consistently.
```
    if (expression) {
        do ..Method(args...)
        set i = j + 1
    } else {
        while (condition) {
            write arg1, arg2, !
        }
    }
```
* For better readablity please insert spaces after comma in argument list, i.e.
```
  Write 1, 2, 3
  Do ..Method(arg1, arg2, argN)
```
* For better readability please insert spaces around assignment. You may align several neighbour assignments according to your tastes, i.e.
```
  #dim index As %Integer = 0
  #dim countOfItems As %Integer = ..Count()
  set j  = k + 1
  set iN = jN \ l
```
