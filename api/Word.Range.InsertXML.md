---
title: Range.InsertXML method (Word)
keywords: vbawd10.chm157155744
f1_keywords:
- vbawd10.chm157155744
ms.prod: word
api_name:
- Word.Range.InsertXML
ms.assetid: daee0fee-01cb-5ad7-f61d-ea6ebec1d04a
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# Range.InsertXML method (Word)

Inserts the specified XML into the document at the specified range, replacing any text contained within the range.


## Syntax

_expression_.**InsertXML** (_XML_, _Transform_)

_expression_ An expression that returns a [Range](./Word.Range.md) object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _XML_|Required| **String**|Specifies the XML to insert. This can be any valid custom XML.|
| _Transform_|Optional| **Variant**|Specifies the XML Transformation (XSLT) used to transform the XML. If omitted, the XML is inserted as custom XML without applying a transform.|

## Return value

Nothing


## Example

The following example inserts the specified XML string into the document at the fifth paragraph. This replaces any text contained within the fifth paragraph.


```vb
Dim strXML As String 
 
strXML = "<"xml version=""1.0""><abc:books xmlns:abc=""urn:books"" " & _ 
 "xmlns:xsi=""https://www.w3.org/2001/XMLSchema-instance"" " & _ 
 "xsi:schemaLocation=""urn:books books.xsd""><book>" & _ 
 "<author>Matt Hink</author><title>Migration Paths of the Red " & _ 
 "Breasted Robin</title><genre>non-fiction</genre>" & _ 
 "<price>29.95</price><pub_date>2006-05-01</pub_date>" & _ 
 "<abstract>You see them in the spring outside your windows. " & _ 
 "You hear their lovely songs wafting in the warm spring air. " & _ 
 "Now follow their path as they migrate to warmer climes in the fall, " & _ 
 "and then back to your back yard in the spring.</abstract></book></abc:books>" 
 
ActiveDocument.Paragraphs(5).Range.InsertXML strXML
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]