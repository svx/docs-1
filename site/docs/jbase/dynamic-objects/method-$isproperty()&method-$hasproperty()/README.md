# Method: $isproperty()
Method: $hasproperty()

**Created At:** 2/15/2018 2:32:30 PM  
**Updated At:** 12/1/2019 1:05:09 PM  
**Original Doc:** [method-isproperty](https://docs.jbase.com/42948-dynamic-objects/method-isproperty)  
**Original ID:** 299334  
**Internal:** No  


## Description

The **$isproperty()** method, and its synonym, **$hasproperty()**, determines if one or more properties, including inherited\* properties, exist in an object or array.

\* See Notes below

## Syntax

```
obj->$isproperty(arg1,{arg2,arg3,...})
arr->%isproperty(index1,{index2,index3,...})
```



## Arguments




| Description<br> |
| --- |
| Each argument is a literal or variable that is checked to see if it is a property of the object or array. The properties of arrays are always the index of the value (see example below).<br> |




## Return values

```
0 = at least 1 of the arguments is not a property
1 = all of the arguments are properties
```



## Examples

```
obj = new object
obj->"timezone" = "EDT"
locale = "en_US"
obj->locale = locale
bool = obj->$isproperty("timezone") ;* bool = 1
crt obj->$isproperty("locale")      ;* Displays 1
locale_text = "locale"
crt obj->$isproperty(locale_text)   ;* Displays 1
bool = obj->$isproperty(locale)     ;* bool = 0 (locale is a local variable, not a property)
crt obj->$isproperty("locale","timezone") ;* Dieplays 1 (all arguments are properties of the object)
crt obj->$isproperty(locale,"timezone")   ;* Displays 0 (locale is not a property)
```

Given the following array with 3 properties:

```
arr = new array
arr->0 = "ian"
arr->1 = "greg"
arr->2 = "daniel"
```

```
crt arr->$isproperty(0)    ;* Displays 1
bool = arr->$isproperty(2) ;* bool = 1
crt arr->$isproperty(1,0)  ;* Displays 1
crt arr->$isproperty(1,2,3);* Displays 0 (2 and 3 are not properties of the array)
```

However, be warned when doing something like this:

```
crt arr->$isproperty("greg")
```

This also displays "1". Because it is an array it tries to convert "greg" to a numeric to get a relative index position. The string "greg" is not numeric so "0" is returned. Hence, in effect, it is looking for index value 0, which exists.



## Notes

The only properties that are inherited are those that are created in the constructor of the inherited class.