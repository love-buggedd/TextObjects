# Introduction to TextObjects
## Credits
This module was created by Matt.

* Roblox → @exqvy
* GitHub → @love.buggedd
* Other → @xyb

## Summary
TextObjects is a module inspired by Defaultio's RichText made in 2017. As of versions 1.0+ customization based on purely scripting is the only available means of customization for the Text Objects.

Let's start by creating a Text Object:
```lua
local TextObjects = require(TextObjects)
local Frame = script.Parent

local TextParameters: TextObjects.TextParameters = {}
local Text = TextObjects.new(
	Frame, 
	TextParameters
)

Text:CreateSequence("Hello, World!")
```
!!! info
    This is the basic constructor for a dynamic Text Label object *(TextObject)*. You're going to be doing a lot—if not all your coding inside of the `TextParameters`; so it's a very important part of your code!
    
    The `Frame` doesn't necessarily have to be an actual frame, as long as it's apart of the `GuiObject` type it'll work.