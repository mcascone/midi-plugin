# midi-plugin
midi utility plugin

## Initial Requirements thoughts

- intercept midi and increment/decrement CC Value by a set amount (default 1), then pass on to output
- The inc/dec value itself is midi controllable
- Keep state of various params to make more advanced decisions about what messages to send
- it's not necessarily about the outgoing messages, it's what the captain configures itself as
  - how would that work in the captain
  - too slow to update files on the fly + reload
  - can the config be reloaded on the fly w/o unmounting or restarting app
 
It could be done in super mode but only in one direction. this allows up/down cc values without statically configuring it in the captain

disabled just passes input to output
