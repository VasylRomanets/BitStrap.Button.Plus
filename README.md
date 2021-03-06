# HandyButtons
Attribute used to draw a button in the Unity Inspector.

The attribute was originally introduced in amazing [BitCake's repository](https://bitbucket.org/bitcake-studio/bitstrap). Then my colleague [dotsquid](https://github.com/dotsquid) took it one step further by implementing the optional 
button name feature. Finally, I put my two cents in and added the execution mode feature.

### Usage
Put the *[Button]* attribute above a method in your MonoBehaviour/ScriptableObject class.

You can specify a button name. By default, a button name corresponds to its method name.
In this example we explicitly specify the button name:
```csharp
[Button("Bar")]
private void Foo()
{ }
```

Also, you can specify when your button is clickable: only in play mode, only in edit mode or both.
By default, a button is clickable in both play mode and edit mode.
In this example the button is clickable only in play mode:
```csharp
[Button(ExecutionMode.PlayModeOnly)]
private void Foo()
{ }
```

### Limitations
Keep in mind these limitations:
* Method can't be generic
* Method can't have parameters
* Classes with custom editors should use helper methods of *ButtonUtility* or inherit from *MonoBehaviourButtonEditor/ScriptableObjectButtonEditor*

### Installation
To add the attribute as a custom package open *YourProject/Packages/manifest.json* and add the following line to the *dependencies* object:
```json
"com.vasylromanets.handybuttons": "https://github.com/VasylRomanets/HandyButtons.git#upm"
```
Or you can simply download the source code and drop it into *YourProject/Assets* folder.

### Example
```csharp
[Button]
private void EditorAndRuntimeButton()
{
    Debug.Log("Editor and runtime!");
}

[Button(ExecutionMode.EditModeOnly)]
private void EditorOnlyButton()
{
    Debug.Log("Editor only!");
}

[Button(ExecutionMode.PlayModeOnly)]
private void RuntimeOnlyButton()
{
    Debug.Log("Runtime only!");
}
```
![Alt text](https://github.com/VasylRomanets/HandyButtons/blob/images/Buttons.gif)
