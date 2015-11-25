# cos-guidelines
There is mandatory and recommended parts. _Recommended part to being formed at the moment_

But here is general advice: use common sense and try to *be consistent* wherever you write code. 
If there is some style already established in the class or utility being modified then we recommend
to continue use that same style, than introducing yet another one, which may be more recommended 
but will produce inconsistent results.

## Mandatory part

1. Only "modern" syntax permitted, dotted syntax is not generally allowed (with few exceptions)
2. No short name for statements keywords allowed - use fully expanded keyword names. This same rule applie to builtin function names - they should be fully pronounced.
 
## Recommended part
1. We recommend to use fully expanded keyword in lower case or capitalized. Whatever you'll select should be consistent across class or utility, i.e.
```
If (expression) {
  Do ##class(Sample).%New(initexpresion)
   For i=1:1:10 {
    Write something, $Zversion, !
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
2. Use the reasonable name convention which is consistent across hierarchy. We recommend to use CamelCase for classes, methods and properties (e.g. `Sample.Person`, `OpenFile`, `LastIndex`, etc.), but smallCamelCase for local variables (e.g. `startDate`, `endDate`), but please be consistent and use local schea if it's different thancurrent recommendation.
3. For better readablity please insert spaces after comma in argument list, i.e.
```
Write 1, 2, 3
Do ..Method(Arg1, Arg2, Arg3)
```
