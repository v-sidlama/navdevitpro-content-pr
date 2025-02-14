---
title: "FIELDNO Function (Record)"
description: FIELDNO Function (Record)
ms.custom: na
ms.date: 06/05/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.prod: "dynamics-nav-2018"
ms.assetid: 940ed8d7-1f28-485c-a996-d4f096354c12
caps.latest.revision: 11
manager: edupont
---
# FIELDNO Function (Record)
Gets the number assigned to a field in the table description.  
  
## Syntax  
  
```  
  
Number := Record.FIELDNO(Field)  
```  
  
#### Parameters  
 *Record*  
 Type: Record  
  
 The name of the record that contains the field.  
  
 *Field*  
 Type: Field  
  
 The name of the field in the record.  
  
## Property Value/Return Value  
 Type: Integer  
  
 The number of the field specified.  
  
## Example 1  
 This example requires that you create the following variables.  
  
|Variable name|DataType|Subtype|  
|-------------------|--------------|-------------|  
|Num|Integer|Not applicable|  
|CustomerRec|Record|Customer|  
  
```  
Num := CustomerRec.FIELDNO("No.");  
```  
  
 This statement assigns the number of the No. field in the CustomerRec record to the number variable.  
  
## Example 2 
 In this example, the **FIELDNO** function is used to determine which field that a variable, which contains a field number, points to in a record. This example requires that you create the following variables.  
  
|Variable name|DataType|Subtype|  
|-------------------|--------------|-------------|  
|CurrentFieldNo|Integer|Not applicable|  
|CustomerRec|Record|Customer|  
  
```  
CASE CurrentFieldNo OF  
  Customer.FIELDNO("No."):   
    ...  
  Customer.FIELDNO(Name):   
    ...  
  Customer.FIELDNO(Address):  
    ...  
  ELSE  
    ...  
END;  
```  
  
 This construct allows you to take actions based on the field number contained in the CurrentFieldNo variable.  
  
## See Also  
 [Record Data Type](Record-Data-Type.md)