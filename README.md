# midi-plugin
midi utility plugin

Keep state of various params to make more advanced decisions about what messages to send.

## Current functionality

### Smart CC increment/decrement

Intercept midi and increment/decrement a CC message's Value by a set amount (default 1), then pass on to output.
- Pretty much the same idea as the existing PC increment/decrement function
- The inc/dec value itself is midi controllable
- disabled just passes input to output

This could be done in the MIDI Captain's **Super Mode**, using the `keypress` feature, but only in one direction. This plugin allows incrementing/decrementing CC values without statically configuring them in the captain (or any other device).

### Use Case

My current thinking is to intercept a single, static CC incoming from a controller.
1. If it's not been set before:
   - Save its current value, or set a starting value, adjustable, midi controllable.
   - If it has been previously set: get the saved value (state).
1. increment the value by a given integer. default 1, adjustable, MIDI controllable.
    - RANDOM option
1. provide a RESET function to start over, unset state; midi controllable
   - maximum value of 127. reset to 0 at 128. reset value same as start value. Max value adjustable, midi controllable.
1. same pattern for decrement.

<!--
## Potential challenges
Multiple ideas here. This project will be universal, not just for the MIDI Captain.

Regarding the Midi Captain, it's not necessarily about the outgoing messages, it's what the captain configures itself as.

Example: if i change a state using a long press, i want that state to be reflected in the LED color when i do a short press.

  - how would that work in the captain
  - too slow to update files on the fly + reload
  - can the config be reloaded on the fly w/o unmounting or restarting app?
    
Probably need access to the source code for the MIDI Captain Ideas.
-->
