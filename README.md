crusher
=======

It's not a player, it just crushes a lot.

###Get Started:

```javascript
var ac = new webkitAudioContext()
  , crusher = new Crusher(ac)
  , url = 'path/to/file.mp3'
  , audio = new Audio()
  , src;

audio.src = url;

audio.addEventListener('canplaythrough', function() {
  src = ac.createMediaElementSource(audio);
  src.connect(crusher.input);
  crusher.connect(ac.destination);
  audio.play();
}, false);
```

###Instantiation

Crusher requires an `AudioContext` on instantiation, and optionally accepts:

####`bits`:
The desired output bit-depth.
####`reduction`:
Ratio of output samplerate to the original samplerate. For example, a `reduction` value of `0.1` 
would result in an output samplerate of 4.41kHz assuming a starting rate of 44.1kHz.

Both `bits` and `reduction` can be modified on-the-fly and updates will be applied in (almost) real-time - 
which is to say that they'll be applied the next time Crusher's `onaudioprocess` callback fires.

Happy crushing!
