---
title: Selection.Application property (PowerPoint)
keywords: vbapp10.chm508001
f1_keywords:
- vbapp10.chm508001
ms.prod: powerpoint
api_name:
- PowerPoint.Selection.Application
ms.assetid: eb1591fe-f6ce-1f9c-21e1-fab39589c527
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# Selection.Application property (PowerPoint)

Returns an **[Application](PowerPoint.Application.md)** object that represents the creator of the specified object.


## Syntax

_expression_.**Application**

_expression_ A variable that represents a [Selection](PowerPoint.Selection.md) object.


## Return value

Application


## Example

In this example, a **[Presentation](PowerPoint.Presentation.md)** object is passed to the procedure. The procedure adds a slide to the presentation and then saves the presentation in the folder where Microsoft PowerPoint is running.


```vb
Sub AddAndSave(pptPres As Presentation)

    pptPres.Slides.Add 1, 1

    pptPres.SaveAs pptPres.Application.Path & "\Added Slide"

End Sub
```

This example displays the name of the application that created each linked OLE object on slide one in the active presentation.




```vb
For Each shpOle In ActivePresentation.Slides(1).Shapes

    If shpOle.Type = msoLinkedOLEObject Then

        MsgBox shpOle.OLEFormat.Application.Name

    End If

Next
```


## See also


[Selection Object](PowerPoint.Selection.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]