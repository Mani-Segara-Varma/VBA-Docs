---
title: Image.SizeToFit method (Access)
keywords: vbaac10.chm10358
f1_keywords:
- vbaac10.chm10358
ms.prod: access
api_name:
- Access.Image.SizeToFit
ms.assetid: 81e403d6-ba9a-9117-1f87-fe6bb4b76d00
ms.date: 02/20/2019
ms.localizationpriority: medium
---


# Image.SizeToFit method (Access)

Use the **SizeToFit** method to size a control so that it fits the text or image that it contains.


## Syntax

_expression_.**SizeToFit**

_expression_ A variable that represents an **[Image](Access.Image.md)** object.


## Remarks

For example, you can apply the **SizeToFit** method to a command button that is too small to display all the text in its **Caption** property.

You can apply the **SizeToFit** method to controls only in form Design view or report Design view.

The **SizeToFit** method makes a control larger or smaller, depending on the size of the text or image that it contains.

Use the **SizeToFit** method in conjunction with the **[CreateControl](Access.Application.CreateControl.md)** method to size new controls that you have created in code.

> [!NOTE] 
> Not all controls that contain text or an image can be sized by the **SizeToFit** method. Several controls are bound to data that can vary in size from one record to the next. These controls include the text box, list box, combo box, and bound object frame controls. The **SizeToFit** method does not apply to controls on data access pages.


## Example

The following example creates a new form and a command button on the form. The procedure then sets the control's **Caption** property and sizes the control to fit the caption.

```vb
Sub SizeNewControl() 
 Dim frm As Form, ctl As Control 
 
 ' Create new form. 
 Set frm = CreateForm 
 ' Create new command button. 
 Set ctl = CreateControl(frm.Name, _ 
 acCommandButton, , , , 500, 500) 
 ' Restore form. 
 DoCmd.Restore 
 ' Set control's Caption property. 
 ctl.Caption = "Extremely Long Control Caption" 
 ' Size control to fit caption. 
 ctl.SizeToFit 
End Sub
```




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]