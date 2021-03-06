---
title: "Modify a Collection | Microsoft Docs"
ms.custom: ""
ms.date: "09/20/2016"
ms.prod: "configuration-manager"
ms.reviewer: ""
ms.suite: ""
ms.technology:
  - "configmgr-other"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to:
  - "System Center Configuration Manager (current branch)"
ms.assetid: 21815cfc-bd5d-4c1e-b2e6-f6662d1cc408
caps.latest.revision: 11
author: "shill-ms"
ms.author: "v-suhill"
manager: "mbaldwin"
---
# How to Modify a Collection
### To Modify a Collection  

1.  Set up a connection to the SMS Provider.  

2.  Get the specific collection instance by using the collection ID provided.  

3.  Display the current property values (name and comment properties used as examples).  

4.  Modify the example property values using the `name` and `comment` values passed in.  

## Example  
 The following example method shows how to modify collection properties.  

 For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../../../develop/core/understand/calling-code-snippets.md).  

```vbs  
Sub RenameCollection(connection, collectionID, name, comment)    Dim collection    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    WScript.Echo "-- Collection " & collectionID & " --"    WScript.Echo "Name before: " & collection.Name    WScript.Echo "Comment before: " & collection.Comment    collection.Name = name    collection.Comment = comment    collection.Put_    WScript.Echo ""    WScript.Echo "Name after: " & collection.Name    WScript.Echo "Comment after: " & collection.CommentEnd Sub  
```  

```c#  
public void RenameCollection(WqlConnectionManager connection, string collectionID, string name, string comment){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    Console.WriteLine("-- Collection {0} --", collectionID);    Console.WriteLine("Name before: {0}", collection["Name"].StringValue);    Console.WriteLine("Comment before: {0}", collection["Comment"].StringValue);    collection["Name"].StringValue = name;    collection["Comment"].StringValue = comment;    collection.Put();    collection.Get();    Console.WriteLine();    Console.WriteLine("Name after: {0}", collection["Name"].StringValue);    Console.WriteLine("Comment after: {0}", collection["Comment"].StringValue);}  
```  

 The example method has the following parameters:  

|Parameter|Type|Description|  
|---------------|----------|-----------------|  
|`connection`|-   Managed: [WqlConnectionManager](assetId:///WqlConnectionManager?qualifyHint=False&autoUpgrade=True)<br />-   VBScript: [SWbemServices](assetId:///SWbemServices?qualifyHint=False&autoUpgrade=True)|A valid connection to the SMS Provider.|  
|collectionID|-   Managed: [String](assetId:///String?qualifyHint=False&autoUpgrade=True)<br />-   VBScript: assetId:///String?qualifyHint=False&autoUpgrade=True|Unique auto-generated ID containing eight characters. For more information, see the CollectionID property of [SMS_Collection Server WMI Class](../../../../develop/reference/core/clients/collections/sms_collection-server-wmi-class.md).|  
|name|-   Managed: assetId:///String?qualifyHint=False&autoUpgrade=True<br />-   VBScript: assetId:///String?qualifyHint=False&autoUpgrade=True|An example collection property. The property value is modified in the code snippet.|  
|comment|-   Managed: assetId:///String?qualifyHint=False&autoUpgrade=True<br />-   VBScript: assetId:///String?qualifyHint=False&autoUpgrade=True|An example collection property. The property value is modified in the code snippet.|  

## Compiling the Code  
 The C# example requires:  

### Namespaces  
 System  

 Microsoft.ConfigurationManagement.ManagementProvider  

 Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine  

### Assembly  
 adminui.wqlqueryengine  

 microsoft.configurationmanagement.managementprovider  

 mscorlib  

## Robust Programming  
 For more information about error handling, see [About Configuration Manager Errors](../../../../develop/core/understand/about-configuration-manager-errors.md).  

## See Also  
 [Configuration Manager Collections](../../../../develop/core/clients/collections/collections.md)   
 [SMS_Collection Server WMI Class](../../../../develop/reference/core/clients/collections/sms_collection-server-wmi-class.md)
