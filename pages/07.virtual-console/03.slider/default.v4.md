---
title: Slider
date: '03:02 22-08-2023'
---

Sliders are used for three distinct purposes: 
* [Fixture](/basics/glossary-and-concepts#fixtures) channel level setting
* [Function](/basics/glossary-and-concepts#functions) playback and intensity adjustment
* Submaster functionality<br>

Any slider can operate on either of these modes and each mode has its own configuration options.

### Configuration

Sliders can be configured with the properties ![](/basics/edit.png) button found in the toolbar or by double clicking the slider itself.

### Configuration - General Tab

The General tab holds all of the slider's properties that are shared between the slider's two modes.

|     |     |
| --- | --- |
| **Slider name** | Change the slider's name. |
| **Widget appearance** | A slider can be displayed as a vertical fader ![](/basics/slider.png) or as a knob ![](/basics/knob.png). The appearance can be changed on the fly. |
| **Value display style** | **Actual**: Display actual DMX (0-255) values<br>**Percentage**: Display percentage values (0-100%) |
| **Slider movement** | **Normal**: Values increase towards the top and decrease towards the bottom of the slider.<br>**Inverted**: Flip the slider upside down so that values increase towards the bottom and decrease towards the top. |
| **Catch up with the external controller input value** | When enabled, this feature will help to control the slider with external controllers that do not support feedback or do not have motorized faders.  <br>For example, when controlling a few sliders in different pages of a Frame with a single fader of an external controller, it's very easy to have "out of sync" positions when switching page.  <br>When this option is enabled, an external controller fader should enter a certain threshold before the slider cursor starts to move, to guarantee a sync state and avoid undesired slider jumps. |
| **External input** | You can attach an external input channel from an input device (like a slider board) to sliders so that you don't always have to use the mouse or touch screen to move sliders.<br><br>**Input universe**: The input universe from which you wish to get input data for the slider.<br>**Input channel**: The individual input channel within the selected input universe that you wish to use for controlling the slider.<br>**Auto Detect**: When toggled, you can just move/press a button/slider/knob on your external input hardware and it will be automatically assigned to the slider. The latest combination is shown on the text boxes when QLC+ receives input data. If you don't see anything in the boxes, your input connection might have a problem that you need to fix first.<br>**Choose...**: Shows the [Select Input Channel](../select-input-channel) dialog that you can use to select an input channel manually. |

### Configuration - Level Tab

If the slider is not currently in Level mode, all you see is a button telling you to click it to switch the slider to Level mode. After you click it, the Level mode properties will be shown.

|     |     |
| --- | --- |
| **Value Range** | **Low limit**: Set the lowest DMX value that can be set by the slider.<br>**High limit**: Set the highest DMX value that can be set by the slider.t<br>**From capability**: You can limit the slider's level value range to a certain capability range within a fixture's channel. When you have any channel value range selected from the fixture list (for example _"Dimmer Control 006 - 128"_) and you click this button, the **low and high limit** of this slider are taken automatically from that capability and are set to 6 and 128, respectively. |
| **Fixture list** | You can select individual channels from this list that contains all channels from all of your fixtures. Those channels that you have placed the tick mark beside will be controlled by this slider. |
| **All** | Clicking this button will select ALL channels from ALL fixtures. |
| **None** | Clicking this button will clear ALL channel selections from ALL fixtures. |
| **Invert** | Invert the current selection. If you have channels 1, 3 and 5 selected from all fixtures, clicking this button will clear channels 1, 3 and 5 and instead select channels 2, 4 and 6 from those fixtures. |
| **By group...** | If you wish to control a specific channel group from ALL fixtures, you can click this button and select the channel group to control. Accepting the dialog will select ALL channels that belong to the selected channel group from ALL fixtures. This is particularly useful if you wish to have common control over, for example, all of your scanners' _intensity_ channels. |
| **Click & Go** | Click & Go is a QLC+ technology which allows you to quickly access fixtures functionalities in a completely visual way. When Click & Go is enabled, a button will appear at the bottom of the slider and with just 2 clicks you will reach the desired result.  <br>The supported modes are:<br><br>**None**: Click & Go disabled. No button will be displayed.<br>**Color**: Single color selection. A gradient of the color controlled by the slider will be displayed, allowing you to jump to the desired color visually.<br>**RGB**: RGB color selection. A RGB Color picker will be displayed, allowing you to pick any color from black to white. 16 preset colors are displayed on the left side for convenience. When selecting a color, the slider value will be placed half way (128). Moving it downward will fade towards black, while moving it upward will fade towards white.<br>**Gobo/Effect**: Gobo/Macro selection. A grid view of the fixture defined macros will be displayed and you will be able to choose a macro from its color, its gobo or its name. When the mouse is over a macro cell, a blue bar will appear, allowing you to choose an intermediate value within the same macro. This is useful for functionalities like Gobo rotation speed. |
| **Monitor the selected channels and update the slider level** | **(EXPERIMENTAL)** By enabled this option, the slider will watch the DMX channels changes and if they assume all the same level, the slider will update accordingly for an immediate visual feedback.  <br>When activating this option, a reset button and an additional level bar will be displayed in the slider layout.  <br>If you interact with the slider while it is monitoring some DMX channels, it will switch into an override state, similar to what happens in Simple Desk. The reset button background will turn to red, indicating that the override is in place, and the right side level bar will continue to indicate the monitoring level.  <br>When pressing the reset button from an override state, the slider will go back to the current monitoring level.  <br>It is possible to associate and external control to the override reset button. |

### Configuration - Playback Tab

If the slider is not currently in Playback mode, all you see is a button telling you to click it to switch to Playback mode. After you click it, the Playback mode properties will be shown.  

When the slider is in playback mode, the slider acts like a combined button and slider. You can start a function AND simultaneously control the function's intensity with the slider. When the slider is at zero, the function is stopped but any value above zero will start the function (unless it has already been started) and simultaneously adjust the function's intensity (if applicable).

A slider in Playback mode will ignore the attached Function fade in and fade out times, so fade transitions will have to be performed manually.  
If you need fade in/out automations together with the control of the Function intensity, then the usage of a ![](/basics/button.png)[Virtual Console Button](../button) in combination with a Slider in Submaster mode is what you're looking for.

|     |     |
| --- | --- |
| **Function** | Displays the function that is currently attached to the slider. |
| ![](/basics/attach.png) | Attach a function to the slider. |
| ![](/basics/detach.png) | Detach the currently attached function. |
| **Flash button** | Shows an additional button ![](/basics/flash.png) underneath the slider cursor. Pressing it will flash the attached Function (any type of it) |

### Configuration - Submaster Tab

If the slider is not currently in Submaster mode, all you see is a button telling you to click it to switch to Submaster mode. After you click it, the slider will be set to work as a submaster.

When a slider is set to Submaster mode, it will control the intensity of every other widget in the same frame (please keep in mind that the main Virtual Console area is a frame too !)  
The intensity of a widget depends on the type of widget itself and which functionality it controls. A submaster will control the intensity of any QLC+ "light emitting" functionality, either a function or single channel levels.  
For example a submaster can control the intensity of a function attached to a [button](../button) or the channel levels associated to a slider in level mode.  
Every widget is controlled by a submaster even if the widget's functionality is not active yet. For example if a submaster is set to 50%, a button pressed afterward will start its associated function with 50% of intensity.