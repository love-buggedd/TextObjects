# Text Parameters
### TextFont
The `TextFont` is used to determine how the Text Object will render its text.
!!! warning
    Avoid using the `Legacy` font, it will mess with scaling and overall text-fitting. The result will not be as pretty as if you were to use compatible fonts.
### TextColor
Changes the base color for the Text Object. All text will this color unless adjusted.
### TextSize
Changes the base size for the Tex Object. Serves as a reference for `pixel scaling` in the `TextScaleRelativeTo` options.
### TextScaled
Toggles if the Text Object's text will be rendered appropriately to `TextScaleRelativeTo`'s value.
### TextScaleRelativeTo
This option has three different modes.

* Relative to `"Screen"`
<sup>Text will scale according to the **screen size.**</sup>

* Relative to `"Parent"`
<sup>Text will scale according to the **Text Object target's size.**</sup>

* Relative to a **Pixel Reference**

This specific mode has two different variations. It can either be a number, or a array containing two numbers. This is a subtype of Screen relative sizing.

1. `TextSize = Screen.AbsoluteSize.Y / ReferenceSize`

2. `TextSize = ( Screen.AbsoluteSize.Y / ReferenceSize ) ^ Growth`
!!! tip
    Pixel Reference scaling is incredibly useful for things like mobile friendliness. Adjusting the growth factor allows for extremely flexible text sizing for all devices! Your playerbase will thank you.

### LetterGrouping
Toggles if the sequencing will use letter grouping (words are put as groups). If not everything is stored as a character, instead of characters in groups (words).
!!! warning
    This will disable `Words` in the `AnimateFunctions`.

### MaxWidth
Sets the MaxWidth to any number, defaults to `math.huge`.

### Padding
Creates a `UIPadding` for the sequence text. Something that almost every dialogue system needs. If you don't want to do it yourself, this'll do it for you! This can either be set to a singular number to be set to every value or you can adjust each individual value.
```lua
Padding = 0.25

--# or

Padding = {
    Top = 0.2,
    Left = 0.3,
    Right = 0.3,
    Bottom = 0.2
}
```

### Alignments
1. XAlignment: `Enum.HorizontalAlignment`
2. YAlignment: `Enum.VerticalAlignment`

Sets the `UIListLayout` alignment settings for the lines.

### Themes
1. Lines: `{{Name: string, Value: any}}`
2. Containers: `{{Name: string, Value: any}}`
3. Letters: `{{Name: string, Value: any}}`

Adjusts the **"theme"** of the three core elements Text Objects render. This basically just allows you to adjust their respective properties individually. _(e.g. Changing the background of letters to visible.)_
```lua
Themes.Letters = {
    {Name = "BackgroundTransparency", Value = 0}
    {Name = "BackgroundColor3", Value = Color3.new(0, 0, 0)}
}
```

### AnimateText
A boolean that toggles if a text is animated. _(User Scripted)_
<sup>Preset animations & entrances will be introduced in update 2.0+</sup>

### AnimateFunctions
1. Letters: `(Letter: TextLabel, number) → ()`
2. Words: `(Word: TextLabel, number) → ()`
3. Lines: `(Line: {Line: Frame, Container: Frame}, number) → ()`

If you're unsure what the text above means, basically each function has two parameters. One with the individual letter, word, or line, and the second parameter being the number of whatever one you're on. Please look at the code below as it contains an important piece of information about the Animate Functions.
```lua
AnimateFunctions = {
    Letters = function (Letter: TextLabel, Index: number)
        -- Code here
    end,

    Words = function (Word: TextLabel, Index: number)
        -- Code here
    end,

    Lines = function (LineTable: {}, Index: number)
        --[[
            Lines are actually tables, containing two instances.
            The actual line, and the container with the words & letters.
        --]]
        local Line = LineTable.Line
        local Container = LineTable.Container

        -- Code here
    end,
}
```

### Spacings
1. LetterSpacing
2. WordSpacing
3. LineSpacing

All of these intake a number, each acting as a multiplier. Think of it as the scale instead of offset of Udim2; just for Text Object spacing.

### OnClick
Calls a function, (scripted by the user) when the Text Object target is pressed.
```lua
OnClick = function (x, y)
    -- Code here
end,
```

### OnHoverEnter
Calls a function whenever the Text Object target is hovered over by the player's mouse.
```lua
OnHoverEnter = function (x, y)
    -- Code here
end,
```

### OnHoverLeave
Calls a function whenever the player's mouse stops hovering the Text Object's target.
```lua
OnHoverLeave = function (x, y)
    -- Code here
end,
```

### OnLongPress
Calls a function when the player clicks for more than half a second.
```lua
OnLongPress = function (x, y)
    -- Code here
end,
```

### OnClickRelease
Calls a function when the player finishes clicking.
```lua
OnClickRelease = function (x, y)
    -- Code here
end,
```

### BeforeText
A function that's called before the sequence is started.
```lua
BeforeText = function ()
    -- Code here
    return nil
end,