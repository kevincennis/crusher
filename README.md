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

###Usage

Crusher requires an `AudioContext` on instantiation, and optionally accepts:

####`bits`:
The desired output bit-depth.
####`reduction`:
Ratio of output samplerate to the original samplerate. For example, a `reduction` value of `0.1` 
would result in an output samplerate of 4.41kHz assuming a starting rate of 44.1kHz.

Both `bits` and `reduction` can be modified on-the-fly and updates will be applied in (almost) real-time - 
which is to say that they'll be applied the next time Crusher's `onaudioprocess` callback fires.

Happy crushing!

License
=======

The MIT License (MIT)

Copyright (c) 2013 Kevin Ennis

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
