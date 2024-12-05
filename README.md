# midi-plugin
midi utility plugin

## Initial Requirements thoughts

1. Intercept midi and increment/decrement a CC message's Value by a set amount (default 1), then pass on to output
    1. Pretty much the same idea as the existing PC increment/decrement function
    1. The inc/dec value itself is midi controllable
    1. disabled just passes input to output
    2. This could be done in the MIDI Captain's `Super Mode`, using the `keypress` feature, but only in one direction. This plugin allows incrementing/decrementing CC values without statically configuring them in the captain (or any other device).

1. Keep state of various params to make more advanced decisions about what messages to send


## Potential challenges
Multiple ideas here. This project will be universal, not just for the MIDI Captain.

Regarding the Midi Captain, it's not necessarily about the outgoing messages, it's what the captain configures itself as.

Example: if i change a state using a long press, i want that state to be reflected in the LED color when i do a short press.

  - how would that work in the captain
  - too slow to update files on the fly + reload
  - can the config be reloaded on the fly w/o unmounting or restarting app?
    
Probably need access to the source code for the MIDI Captain Ideas.
 

