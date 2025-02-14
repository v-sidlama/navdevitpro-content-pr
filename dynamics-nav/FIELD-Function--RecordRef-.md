---
title: "FIELD Function (RecordRef)"
description: FIELD Function (RecordRef)
ms.custom: na
ms.date: 06/05/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.prod: "dynamics-nav-2018"
ms.assetid: 0cbf5999-d63e-49b1-91c3-ce22b194c497
caps.latest.revision: 13
---
# FIELD Function (RecordRef)
Gets a FieldRef for the field that has the number *FieldNo* in the table that is currently selected. If no field has this number, the function returns an error.  
  
## Syntax  
  
```  
  
FieldRef := RecordRef.FIELD(FieldNo)  
```  
  
#### Parameters  
 *RecordRef*  
 Type: RecordRef  
  
 The RecordRef of the record for which you want the fieldref.  
  
 *FieldNo*  
 Type: Integer  
  
 The number that the field has in the table that is currently selected. This is the field for which you want the fieldref.  
  
## Property Value/Return Value  
 Type: FieldRef  
  
## Remarks  
 This function returns an error if the record is not opened and if the field is not found.  
  
 You might obtain better performance by using the [FIELDINDEX Function \(RecordRef\)](FIELDINDEX-Function--RecordRef-.md).  
  
## Example  
 The following example opens table 18 \(Customer\) as a RecordRef variable that is named MyRecordRef. MyRecordRef uses the FIELD function to create a reference to the No. field \(field 1\). The value in the No. field is then set to a specified record No. In this example, the record is set to 30000. The [FIND Function \(RecordRef\)](FIND-Function--RecordRef-.md) function searches the records for record 30000. If record is found, the FIELD function retrieves the value in the Name field \(field 2\), stores it in the varOldName variable and displays it in a message box. The [VALUE Function \(FieldRef, TestPage Field\)](VALUE-Function--FieldRef--TestPage-Field-.md) changes the value in the Name field to a new name. In this example, the new name is ‘Contoso’. The table is then modified to reflect this change and the new value in the Name field is retrieved and displayed in a message box. You can specify any record in the table and change the value in the Name field. This example requires that you create the following variables in the **C/AL Globals** window.  
  
  
  
|Name|DataType|
|-|-|  
|MyRecordRef|RecordRef|  
|MyFieldRef|FieldRef|  
|varOldName|FieldRef|  
|varNewName|Text|  
|MyRecord|Code|  
  
```  
  
MyRecord := '30000';  
varNewName := 'Contoso';  
MyRecordRef.OPEN(18);  
MyFieldRef := MyRecordRef.FIELD(1);  
MyFieldRef.VALUE := MyRecord;  
IF MyRecordRef.FIND('=') THEN BEGIN  
  varOldName := MyRecordRef.FIELD(2);  
  MESSAGE('Old Name: %1', varOldName);  
  varOldName.VALUE := varNewName;  
  MyRecordRef.MODIFY;    
  MESSAGE('New Name: %1', MyRecordRef.FIELD(2));  
END;  
  
```  
  
## See Also  
 [RecordRef Data Type](RecordRef-Data-Type.md)