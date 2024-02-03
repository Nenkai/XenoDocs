# Bdat OC/Object

---

## :material-new-box: Constructor

`oc bdat(string name)`

Creates a new bdat object based on the specified file name.

---

## Methods

### :material-function: getVal

`object bdat->getVal(string columnName, int id)`

Gets a bdat value. Return type depends on column type.

---

### :material-function: getArrayVal

`object bdat->getArrayVal(string columnName, int id, int arrayIndex)`

Gets a bdat value from array. Return type depends on column type.

---


### :material-function: getArrayCount

`int bdat->getArrayCount(string columnName)`

Gets the array size for the specified column.

---


### :material-function: getVarType

`int bdat->getVarType(string columnName)`

Gets the type of the specified column.

---


### :material-function: getIdCount

`int bdat->getIdCount()`

Gets the number of ids/rows in the current bdat file.

---


### :material-function: getIdTop

`int bdat->getIdTop()`

Gets the first id in the current bdat file.

---


### :material-function: getFlagValue

`int bdat->getIdTop(string column, int id, string flagName)`

Gets a flag value.