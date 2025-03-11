# TextObjects
## Constructors
### new
```lua
local Text = TextObjects.new(Target, TextParameters)
```
This constructor (and only constructor) declares a Text Object. All sequences created by this Object will be created according to everything inside of the `TextParameters` table. The `Target`, being the first parameter of the constructor is where the text will be rendered. _(Takes any **GuiObject**)_
## Methods
### CreateSequence
```lua
Text:CreateSequence("Hello, World!")
```
Creates and automatically plays the text sequence with the provided text (in parameter one). This module organizes your inputted text into the `Target` parent; and proceeds to output the created elements according to the `TextParameters`.
---
### DestroySequence
```lua
--# Destroys the text instantly
Text:DestroySequence()

--# Customized destruction
Text:DestroySequence(function()
    --[[
        Animation code here

        Example code below
    --]]
    local DeathTime = 1
    for _, Letter in ipairs(Text.__letters) do
        game:GetService("TweenService"):Create(
            Letter,
            TweenInfo.new(DeathTime),
            {TextTransparency = 1}
        ):Play()
    end
    
    wait(DeathTime)
end)
```
Without an inputted function (executes before everything else if added) the Sequence will completely destroy itself. Adding the function parameter allows you to customize what the sequence does before being destroyed. Like the example code, where it fades out all the text at once before deleting everything.
## Events
### SequenceEnded
```lua
Text.SequenceEnded:Fire()

Text.SequenceEnded:Connect(function()
    -- Code here
end)
```
In the `TextParameters`, if AnimateText—a boolean is set to false (for notice that's the default) the SequenceEnded event will fire instantaneously. If not, then the user has to manually fire it. Likely in the `AnimateFunctions`.