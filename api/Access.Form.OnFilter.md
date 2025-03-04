---
title: Form.OnFilter property (Access)
keywords: vbaac10.chm13459
f1_keywords:
- vbaac10.chm13459
ms.prod: access
api_name:
- Access.Form.OnFilter
ms.assetid: 4d1b52cb-0f79-d8e9-05b3-a7a1da0a7a62
ms.date: 03/14/2019
ms.localizationpriority: medium
---


# Form.OnFilter property (Access)

Sets or returns the value of the **On Filter** box in the Properties window of a form. Read/write **String**.


## Syntax

_expression_.**OnFilter**

_expression_ A variable that represents a **[Form](Access.Form.md)** object.


## Remarks

This property is helpful for programmatically changing the action that Microsoft Access takes when an event is triggered. For example, between event calls you may want to change an expression's parameters, or switch from an event procedure to an expression or macro, depending on the circumstances under which the event was triggered. 

The **Filter** event occurs when a form is opened and its records are displayed.

The **OnFilter** value will be one of the following, depending on the selection chosen in the Choose Builder window (accessed by choosing the **Build** button next to the **On Filter** box in the form's Properties window):

- If you choose Expression Builder, the value will be =_expression_, where _expression_ is the expression from the Expression Builder window.
    
- If you choose Macro Builder, the value is the name of the macro. 
    
- If you choose Code Builder, the value will be [Event Procedure]. 
    
If the **On Filter** box is blank, the property value is an empty string.


## Example

The following example associates the **Filter** property for the **Order Entry** form to the event **Form_Filter**.

```vb
Forms("Order Entry").OnFilter = "[Event Procedure]"
```


[!include[Support and feedback](~/includes/feedback-boilerplate.md)]