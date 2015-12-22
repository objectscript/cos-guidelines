# Cheat sheet
Some most encountered COS expressions

## Object/SQL Basics  

|      Action                                  |   Code                                                                            |
|----------------------------------------------|-----------------------------------------------------------------------------------|
| Call a class method                          | `Do ##class(package.class).method(arguments)`<br>`Set variable = ##class(package.class).method(arguments)`<br>Note: place a . before each pass-by-reference argument |
| Call an instance method                      | `Do object.method(arguments)`<br>`Set variable = object.method(arguments)`<br>Note: place a . before each pass-by-reference argument |
| Create a new object                          | `Set object = ##class(package.class).%New()`                                      |
| Open an existing object                      | `Set object = ##class(package.class).%OpenId(id, concurrency, .status)`           |
| Save an object                               | `Set status = object.%Save()`                                                     |
| Retrieve the ID of a saved object            | `Set id = object.%Id()`                                                           |
| Retrieve the OID of a saved object           | `Set oid = object.%Oid()`                                                         |
| Validate an object without saving            | `Set status = object.%ValidateObject()`                                           |
| Validate a property without saving           | `Set status = ##class(package.class).PropertyIsValid(object.Property)`            |
| Print status after error                     | `Do $system.Status.DisplayError(status)`<br>`ZWrite status` (v2012.2+)            |
| Obtain status details after error            | `Do $system.Status.DecomposeStatus(status, .err)`                                 |
| Remove an object from process memory         | `Set object = ""`                                                                 |
| Delete an existing object of a class         | `Set status = ##class(package.class).%DeleteId(id)`                               |
| Delete all saved objects of a class          | `Do ##class(package.class).%DeleteExtent()`<br>`Do ##class(package.class).%KillExtent()` |
| Reload properties of a saved object          | `Do object.%Reload()`                                                             |
| Clone an object                              | `Set clonedObject = object.%ConstructClone()`                                     |
| Write a property                             | `Write object.property`                                                           |
| Set a property                               | `Set object.property = value`                                                     |
| Set a serial (embedded) property             | `Set object.property.embeddedProperty = value`                                    |
| Link two objects                             | `Set object1.referenceProperty = object2`                                         |
| Populate a class                             | `Do ##class(package.class).Populate(count, verbose)`                              |
| Remove all objects in process memory         | `Kill`                                                                            |
| List all objects in process memory           | `Do $system.OBJ.ShowObjects()`                                                    |
| Display all properties of an object          | `Do $system.OBJ.Dump(object)`<br>`Zwrite object` (v2012.2+)                              |
| Determine If variable is an object reference | `If $isobject(variable) ; 1=yes, 0=no`                                              |
| Find classname of an object                  | `Write $classname(oref)`                                                            |
| Start the SQL shell                          | `Do $system.SQL.Shell()`                                                            |
| Test a class query                           | `Do ##class(%ResultSet).RunQuery(class, query)`                                     |

## ObjectScript Commands 

| Command                       | Description                                                                         |
|-------------------------------|-------------------------------------------------------------------------------------|
| `Write`                       | Display text strings, value of variable or expression.                              |
| `Set`                         | Set value of variable.                                                              |
| `Do`                          | Execute method, procedure, or routine.                                              |
| `Quit` or `Return` (v2013.1)  | Terminate method, procedure, or routine. Optionally return value to calling method. |
| `Halt`                        | Stop Caché process and close Terminal.                                              |
| `Kill`                        | Destroy variable(s).                                                                |
| `If {} ElseIf {} Else {}`     | Evaluate conditions and branch.                                                     |
| `For {}`, `While {}`, `Do {} While` | Execute block of code repeatedly.                                             |
| `Try {} Catch {}`, `Throw`    | Handle errors.                                                                      |

## ObjectScript Functions

| Action                                           | Code                                                        | 
|--------------------------------------------------|-------------------------------------------------------------| 
| Date conversion (external → internal)            | `Set variable = $zdh("mm/dd/yyyy")`                         | 
| Date conversion (internal → external)            | `Set variable = $zd(internalDate, format)`                  | 
| Time conversion (external → internal)            | `Set variable = $zth("hh:mm:ss")`                           | 
| Time conversion (internal → external)            | `Set variable = $zt(internalTime, format)'                  | 
| Display current internal date/time string        | `Write $horolog`                                            | 
| Display UTC date/time string                     | `Write $ztimestamp`                                         | 
| Display length of a string                       | `Write $length(string)`                                     | 
| Build a list                                     | `Set listString = $listbuild(list items, separated by comma)` | 
| Retrieve an item from a list                     | `Set variable = $list(listString, position)`                | 
| Display the length of a list                     | `Write $listlength(listString)`                             | 
| Display random integer from start to start+count | `Write $random(count) + start`                              | 
| Check if variable exists                         | `Write $data(variable)`                                     | 
| Return value of variable, or "" If undefined     | `Write $get(variable)`                                      | 

## Collections

| Action                                                       | Code                                                                                                   |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Create a new standalone list<br>Work with a list property    | `Set listObject=##class(%ListOfDataTypes).%New()`<br>Use methods below on a list collection property     |
| Insert an element at the end of a list                       | `Do listObject.Insert(value)`<br>`Do object.listProperty.Insert(value)`                                    |
| Insert an element into a list                                | `Do listObject.SetAt(value, position)`<br>`Do object.listProperty.SetAt(value, position)`                  |
| Remove an element from a list                                | `Do listObject.RemoveAt(position)`<br>`Do object.listProperty.RemoveAt(position)`                          |
| Display an element of a list                                 | `Write listObject.GetAt(position)`<br>`Write object.listProperty.GetAt(position)`                          |
| Display the size of a list                                   | `Write listObject.Count()`<br>`Write object.listProperty.Count()`                                          |
| Clear all the elements of a list                             | `Do listObject.Clear()`<br>`Do object.listProperty.Clear()`                                                |
| Create a new standalone array<br>Work with an array property | `Set arrayObject=##class(%ArrayOfDataTypes).%New()`<br>Use methods below on an array collection property |
| Insert an element into an array                              | `Do arrayObject.SetAt(value, key)`<br>`Do object.arrayProperty.SetAt(value, key)`                          |
| Remove an element from an array                              | `Do arrayObject.RemoveAt(key)`<br>`Do object.arrayProperty.RemoveAt(key)`                                  |
| Display an element of an array                               | `Write arrayObject.GetAt(key)`<br>`Do object.arrayProperty.GetAt(key)`                                     |
| Display the size of an array                                 | `Write arrayObject.Count()`<br>`Do object.arrayProperty.Count()`                                           |
| Clear all elements of an array                               | `Do arrayObject.Clear()`<br>`Do object.arrayProperty.Clear()`                                              |

## Relationships

| Action                                  | Code                                                                                     |
|-----------------------------------------|------------------------------------------------------------------------------------------|
| Parent-to-children object linking       | `Do parentObject.childRefProperty.Insert(chilDobject)`<br>`Set chilDobject.parentRefProperty = parentObject` |
| One-to-many object linking              | `Do oneObject.manyRefProperty.Insert(manyObject)`<br>`Set manyObject.OneRefProperty = OneObject`             |
| Write a property of a child object      | `Write parentObject.childRefProperty.GetAt(position).property`                           |
| Write a property of a many object       | `Write oneObject.manyRefProperty.GetAt(position).property`                               |
| Display the count of child/many objects | `Write parentObject.childRefProperty.Count()`<br>`Write oneObject.manyRefProperty.Count()` |
| Open a many/child object directly       | `Set object = ##class(package.class).IDKEYOpen(parentID, childsub)`                      |
| Retrieve the id of a child object       | `Set status = ##class(package.class).IDKEYExists(parentID, childsub, .childID)`          |
| Clear the child/many objects            | `Do parentObject.childRefProperty.Clear()<br>Do oneObject.manyRefProperty.Clear()`       |

## Streams

| Action                                    | Code                                                                                  |
|-------------------------------------------|---------------------------------------------------------------------------------------|
| Create a new stream                       | `Set streamObject=##class(%Stream.GlobalCharacter).%New()`<br>`Set streamObject=##class(%Stream.GlobalBinary).%New()`<br>Use methods below on a stream property |
| Add text to a stream                      | `Do streamObject.Write(text)`<br>`Do object.streamProperty.Write(text)`               |
| Add a line of text to a stream            | `Do streamObject.WriteLine(text)`<br>`Do object.streamProperty.WriteLine(text)`       |
| Read len characters of text from a stream | `Write streamObject.Read(len)`<br>`Write object.streamProperty.Read(len)`             |
| Read a line of text from a stream         | `Write streamObject.ReadLine(len)`<br>`Write object.streamProperty.ReadLine(len)`     |
| Go to the beginning of a stream           | `Do streamObject.Rewind()`<br>`Do object.streamProperty.Rewind()`                     |
| Go to the end of a stream, for appending  | `Do streamObject.MoveToEnd()`<br>`Do object.streamProperty.MoveToEnd()`               |
| Clear a stream                            | `Do streamObject.Clear()`<br>`Do object.streamProperty.Clear()`                       |
| Display the length of a stream            | `Write streamObject.Size`<br>`Write object.streamProperty.Size`                       |

## Unit Testing Macros

| Action                      | Code                                             |
|-----------------------------|--------------------------------------------------|
| Assert equality             | `Do $$$AssertEquals(value1, value2, message)`    |
| Assert inequality           | `Do $$$AssertNotEquals(value1, value2, message)` |
| Assert status is OK         | `Do $$$AssertStatusOK(status, message)`          |
| Assert status isn't OK      | `Do $$$AssertStatusNotOK(status, message)`       |
| Assert condition is true    | `Do $$$AssertTrue(condition, message)`           |
| Assert condition isn't true | `Do $$$AssertNotTrue(condition, message)`        |
| Log message                 | `Do $$$LogMessage(message)`                      |

## Other Macros

| Action                           | Code                                      |
|----------------------------------|-------------------------------------------|
| Return a good status             | `Quit $$$OK`                              |
| Return an error status           | `Quit $$$ERROR($$$GeneralError, message)` |
| Throw exception on error         | `$$$ThrowOnError(status, code)` or `$$$TOE(status, code)` |
| Check if status is good          | `If $$$ISOK(status)`                      |
| Check if status is an error      | `If $$$ISERR(status)`                     |
| Return a null object reference   | `Quit $$$NULLOREF`                        |
| Place a new line within a string | `Write string1_$$$NL_string2`             |
