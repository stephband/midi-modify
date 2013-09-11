# midi-modify

Modifiers browser MIDI events.


## Instantiation

Create a filter:

    var midiModify = new MIDIModify(options);

This creates a modify node.
The <code>new</code> keyword is optional.


### node.in(e)

To pass messages into the filter, call the filter's <code>in</code> method:

    midiModify.in(e);


### node.out(fn)

To listen to the output, register a listener with the filter's <code>out</code> method:

    midiModify.out(fn);

The callback function <code>fn</code> will be called whenever a MIDI message is passed
through the modifier. It is given the message <code>e</code> as it's first argument.


## Options

A modifier understands the options:

    {
        port:    number | string | target
        channel: number (1-16) | fn
        message: string
        data1:   number (0-127) | fn
        data2:   number (0-127) | fn
    }

<code>message</code> should be one of:

	'noteoff'
	'noteon'
	'polytouch'
	'cc'
	'pc'
	'channeltouch'
	'pitch'

Functions should return a number.