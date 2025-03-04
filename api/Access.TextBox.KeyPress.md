---
title: TextBox.KeyPress event (Access)
keywords: vbaac10.chm14207
f1_keywords:
- vbaac10.chm14207
ms.prod: access
api_name:
- Access.TextBox.KeyPress
ms.assetid: 87db62a8-30f6-03d8-63ae-f1a1a50caea3
ms.date: 02/10/2019
ms.localizationpriority: medium
---


# TextBox.KeyPress event (Access)

The **KeyPress** event occurs when the user presses and releases a key or key combination that corresponds to an ANSI code while a form or control has the focus. This event also occurs if you send an ANSI keystroke to a form or control by using the SendKeys action in a macro or the **SendKeys** statement in Visual Basic.


## Syntax

_expression_.**KeyPress** (_KeyAscii_)

_expression_ A variable that represents a **[TextBox](Access.TextBox.md)** object.


## Parameters

|Name|Required/Optional|Data type|Description|
|:-----|:-----|:-----|:-----|
| _KeyAscii_|Required|**Integer**| Returns a numeric ANSI key code. The _KeyAscii_ argument is passed by reference; changing it sends a different character to the object. Setting the _KeyAscii_ argument to 0 cancels the keystroke so that the object doesn't recognize that a key was pressed.|

## Remarks

To run a macro or event procedure when this event occurs, set the **OnKeyPress** property to the name of the macro or to [Event Procedure].

The object with the focus receives all keystrokes. A form can have the focus only if it has no controls or all its visible controls are disabled.

A form will also receive all keyboard events, even those that occur for controls, if you set the **KeyPreview** property of the form to Yes. With this property setting, all keyboard events occur first for the form, and then for the control that has the focus. You can respond to specific keys pressed in the form, regardless of which control has the focus. For example, you may want the key combination Ctrl+X to always perform the same action on a form.

If you press and hold down an ANSI key, the **KeyDown** and **KeyPress** events alternate repeatedly (**KeyDown**, **KeyPress**, **KeyDown**, **KeyPress**, and so on) until you release the key, and then the **KeyUp** event occurs.

A **KeyPress** event can involve any printable keyboard character, the Ctrl key combined with a character from the standard alphabet or a special character, and the Enter or Backspace key. Use the **KeyDown** and **KeyUp** event procedures to handle any keystroke not recognized by the **KeyPress** event, such as function keys, navigation keys, and any combinations of these with keyboard modifiers (Alt, Shift, or Ctrl keys). Unlike the **KeyDown** and **KeyUp** events, the **KeyPress** event doesn't indicate the physical state of the keyboard; instead, it indicates the ANSI character that corresponds to the pressed key or key combinations.

**KeyPress** interprets the uppercase and lowercase of each character as separate key codes and, therefore, as two separate characters.

> [!NOTE] 
> The Backspace key is part of the ANSI character set, but the Delete key isn't. If you delete a character in a control by using the Backspace key, you cause a **KeyPress** event; if you use the Delete key, you don't.

The **KeyDown** and **KeyPress** events occur when you press or send an ANSI key. The **KeyUp** event occurs after any event for a control caused by pressing or sending the key. If a keystroke causes the focus to move from one control to another control, the **KeyDown** event occurs for the first control, while the **KeyPress** and **KeyUp** events occur for the second control.

For example, if you go to a new record and type a character in the first control in the record, the following events occur:

- **Current** (for the new record)
- **Enter** (for the first control in the new record)
- **GotFocus** (for the control)
- **KeyDown** (for the control)
- **KeyPress** (for the control)
- **BeforeInsert** (for the new record in the form)
- **Change** (for the control if it's a text box or combo box)
- **KeyUp** (for the control)


## Example

The following example converts text entered in a text box to uppercase as the text is typed in, one character at a time.

To try the example, add the following event procedure to a form that contains a text box named **ShipRegion**.

```vb
Private Sub ShipRegion_KeyPress(KeyAscii As Integer) 
 Dim strCharacter As String 
 
 ' Convert ANSI value to character string. 
 strCharacter = Chr(KeyAscii) 
 ' Convert character to upper case, then to ANSI value. 
 KeyAscii = Asc(UCase(strCharacter)) 
End Sub
```



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
