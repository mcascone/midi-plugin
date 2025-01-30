# midi-plugin

midi utility plugin

Keep state of various params to make more advanced decisions about what messages to send.

## Current functionality ideas

### Feature: Smart CC increment/decrement

Intercept midi and increment/decrement a CC message's Value by a set amount (default 1), then pass on to output.

- Pretty much the same idea as the existing PC increment/decrement function
- The inc/dec value itself is midi controllable
- disabled just passes input to output

This could be done in the MIDI Captain's **Super Mode**, using the `keypress` feature, but only in one direction. This plugin allows incrementing/decrementing CC values without statically configuring them in the captain (or any other device).

#### Design

My current thinking is to intercept a single, static CC incoming from a controller.

1. Configure the trigger CC.
1. If it's not been set before:
   - Save its current value, or set a starting value, adjustable, midi controllable.
   - If it has been previously set: get the saved value (state).
1. Increment the value by a given integer. Default 1, adjustable, MIDI controllable.
    - RANDOM option
1. provide a RESET function to start over, unset state; midi controllable
   - maximum value of 127. reset to 0 at 128. reset value same as start value. Max value adjustable, midi controllable.
1. same pattern for decrement.

### Feature: Auto Ramp

Accept a single CC as a trigger to sweep a CC value up or down.

- Configurable speed.
- Looping option.
- Random option.
- Waveform options (sine, square, triangle, etc)
- Max Value configurable, default 127/0
- Stop/Reset options:
  - Reset to 0 when stopped
  - Ramp to max when stopped
  - Stay at current value when stopped
  - Ramp up/down to 0 (or max) when stopped (configurable ramp speed)

### Feature: Timed/Repeat Send

Sends a CC/PC/etc at timed intervals.

- Configurable for one-shot or looping behavior.
- Configurable number of repeats.
- Can be fed into any of the other features (auto-increment, auto-ramp, etc)
- Can be timed or triggered on CC input.60646


<!-- ## Thoughts regarding the MIDI Captain

Multiple ideas here. This project will be universal, not just for the MIDI Captain.

Regarding the Midi Captain, it's not necessarily about the outgoing messages, it's what the captain configures itself as.

Example: if I change a state using a long press, I want that state to be reflected in the LED color when I do a short press.

- how would that work in the captain
- too slow to update files on the fly + reload
- can the config be reloaded on the fly w/o unmounting or restarting app?

Probably need access to the source code for the MIDI Captain Ideas. -->


## Other Tools

This might be implementable in another form using https://github.com/gbevin/ReceiveMIDI and https://github.com/gbevin/SendMIDI.

These CLI apps allow scripted MIDI messaging and state management.
