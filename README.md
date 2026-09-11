# RoconUI
Welcome to RoconUI, a Simple and Customizable Icon Pack for Roblox UI with **over 1,600 icons**.

RoconUI allows you to seamlessly integrate a variety of icons across your UI workspace, including when using effects such as `UIStroke`, _without needing to use ImageLabels_. RoconUI utilizes the built in Builder Icons, making it an easy way to use these little-known gems.

# Download: 
- Github: https://github.com/CodeBro29/RoconUI
- Roblox Creator Store: https://create.roblox.com/store/asset/122179257249627/RoconUI

# Usage:
RoconUI has two components: the icon list (`RoconUI.Rocons`), and the icon generator (`RoconUI.new`).

The `RoconUI.new()` function returns a string and takes in **one required parameter**, and **two optional parameters**:

- Rocon Name (required): string
- Rocon Color (optional): Color3
- Rocon Size (optional): number

To generate a new Rocon, use the following:

```luau
local RoconUI = require(RoconUI) --Replace with the path to the module.

local Rocon = RoconUI.new(RoconUI.Rocons.robux) --Use the RoconUI.Rocons dictionary to ensure that the icon exists with help from intellisense.
TextButton.Text = `{Rocon} 250`
```
<img width="774" height="189" alt="image" src="https://github.com/user-attachments/assets/359e798b-5534-4a4a-a4d6-3a51d9dbd992" />


**IMPORTANT:** in order to work, the TextLabel or TextButton that the Rocon is being applied to **must have RichText Enabled.**

There are two ways that you can apply Rocons: 
1. Command Bar
   
   Below is an example of applying a star icon to a TextLabel with the command bar. This ensures that the Rocon is already applied when Players join the game.
   <img width="730" height="225" alt="image" src="https://github.com/user-attachments/assets/bcc5195b-4451-4fb8-bd5d-e8993f96015d" />

2. Scripts
   
   You can apply Rocons dynamically using scripts. An example script is written below.
   ```luau
   local RoconUI = require(game.ReplicatedStorage.Packages.RoconUI)
   local LocalPlayer = game.Players.LocalPlayer
   local Label = LocalPlayer.PlayerGUI.Test.NameLabel
   
   Label.Text = `{RoconUI.new(RoconUI.Rocons.personFilled)} @{LocalPlayer.Name}`
   ```
   
# Variants:
Each icon has **2 variants:** a normal icon, and a filled icon.

```luau
RoconUI.new(RoconUI.Rocons.robloxPlus) --Icon unfilled.
RoconUI.new(RoconUI.Rocons.robloxPlusFilled) --Same icon, this time filled.
```

**Exception:** because the icon is filled in blue by default, the `"verifiedBlueFilled"` Rocon does not have an unfilled variant, nor does it accept the optional color parameter. Additionally, because of the specific type of icon this is, strokes will not be applied.
<img width="969" height="174" alt="image" src="https://github.com/user-attachments/assets/be13a3c4-83a5-4006-a354-52dc0f0307a1" />
If customization is needed for the verified icon, a workaround will be given at the end.

# Customization:
You can further customize your Rocon with the optional parameters:

```luau
RoconUI.new(RoconUI.Rocons.robloxPlusFilled, Color3.new(1,0,1)), --Sets the color, but not the size.
RoconUI.new(RoconUI.Rocons.robloxPlusFilled, nil, 20), --Sets the size, but not the color.
RoconUI.new(RoconUI.Rocons.robloxPlusFilled, Color3.new(1,0,1), 30), --Sets the color and the size.
```
<img width="1013" height="226" alt="image" src="https://github.com/user-attachments/assets/33a9417d-6c98-4051-ae17-f0ac6c14a869" />

# Icon List:
I created this module after finding a [DevForum post](https://devforum.roblox.com/t/customize-your-guis-with-builder-icons/3968755) by @82_O7 about Builder Icons. That post links to a helpful list of the most recent icons, which you can view here: https://voxlenox.github.io/RobloxBuilderIconList/

Keep in mind that the Rocons dictionary is camelCase, not hyphenated. 

# Closing Thoughts:
If you have any feedback, feel free to post an issue on this repo. You may also contribute if you'd like. Additionally, if any changes are made to the original source code, as per the license, you must open source the changes.

# Verified Customization Workaround:
As promised, here are a couple of workarounds if you need to customize the verified icon. 

1. Use the `verifiedMonoFilled` Rocon:
  This workaround uses a TextLabel and a Frame. The TextLabel contains the `verifiedMonoFilled` Rocon, with any customization needed. Then, a Frame with a lower ZIndex is placed underneath it, acting as the checkmark. However, this workaround looks sloppy when combined with a UIStroke.
  <img width="800" height="450" alt="ezgif com-video-to-gif-converter" src="https://github.com/user-attachments/assets/b39dcc3d-8577-412b-b455-dab641442b23" />
  
2. Use the `verifiedBackplateFilled` and `verifiedCheckFilled` Rocons:
   This workaround uses two TextLabels: one that has the `verifiedBackplateFilled` Rocon with any other needed text, as well as a `verifiedCheckFilled` Rocon that sits on top of the other TextLabel (using a higher ZIndex). Refer to the image below to see my setup/code.
   <img width="1651" height="727" alt="image" src="https://github.com/user-attachments/assets/a3cb0e6a-b5f9-4b89-b3e3-1a303cd64144" />

Of course, both of these workarounds may look messy on different devices, so keep scaling in mind if you try either of these. 
