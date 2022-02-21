---
layout: post
title:  "Roland Go Bluetooth Woe"
date:   2022-02-21 19:30:17 +0100
categories: blog
tags: music hardware
---

Since I bought my new flat and I have a bit more space, I've been coveting a digital piano. I'm a fairly terrible piano player, but we had a piano when I was a kid and I miss being able to wander over to it and inexpertly thump the keys. A digital piano means I get to do that, but with headphones so I don't make so many enemies in my neighbourhood.

So, I bought a £200 used [Roland Go Piano](https://www.roland.com/uk/products/gopiano_go-61p/). I expect proper pianists would be sniffy about its keys being unweighted and a couple of octaves worth of them being absent, but I enjoy playing it. It feels adequately piano-like, to me. Can't compare it with any other digital piano because I've almost never played another one. A possibly unreasonable whinge I have is that it takes a few seconds to boot up - not long but instant-on would make it slightly more tempting to fondle the keys whenever I walk past it, like with a real piano.

It doesn't have many sounds but I mostly just play the default piano, and there are decent Rhodes and Hammond-ish sounds a keypress away. Also a flute sound that makes it impossible to resist playing the intro to Strawberry Fields Forever. It'd be nice to connect it up to more sounds via the advertised bluetooth midi, and herein lies my greatest frustration.

All the instructions I can find for the bluetooth seem to be about connecting to Android or iOS devices. I can't find any reports of anybody successfully using bluetooth to connect to a PC. On Ubuntu, pairing seems to go fine, and after rebuilding bluez with `--enable-midi` it shows up in the list of alsa midi devices:

```
$ aseqdump -l
 Port    Client name                      Port name
  0:0    System                           Timer
  0:1    System                           Announce
 14:0    Midi Through                     Midi Through Port-0
 24:0    Virtual Raw MIDI 2-0             VirMIDI 2-0
 25:0    Virtual Raw MIDI 2-1             VirMIDI 2-1
 26:0    Virtual Raw MIDI 2-2             VirMIDI 2-2
 27:0    Virtual Raw MIDI 2-3             VirMIDI 2-3
128:0    GO:PIANO MIDI                    GO:PIANO MIDI Bluetooth
```

But, I can't seem to get any event data from it. If I do `aseqdump -p 128:0` and hit the keys, I see nothing. I also tried on Windows with loopmidi and midiberry (which seems to be what everybody suggests), and had similarly disappointing results. At which point, I'm thinking I'll take the cowards way out and buy a long USB cable instead. Do please email me if you've managed to get this device working with bluetooth midi on either Linux or Windows.
