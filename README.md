# midi-filter

Filters browser MIDI events.


## Instantiation

Create a filter:

    var midiFilter = new MIDIFilter(options);

This creates a filter node.
The <code>new</code> keyword is optional.


### node.in(e)

To pass messages into the filter, call the filter's <code>in</code> method:

    midiFilter.in(e);


### node.out(fn)

To listen to the output, register a listener with the filter's <code>out</code> method:

    midiFilter.out(fn);

The callback function <code>fn</code> will be called whenever a MIDI message matches
the filter options. It is passed the message <code>e</code> as it's first argument.


## Options

A filter understands the options:

    {
        port:    number | string | target
        channel: number (1-16) | fn
        message: string | fn
        data1:   number (0-127) | fn
        data2:   number (0-127) | fn
    }

If <code>port</code> is a number, the message is filtered by <code>e.target.id</code>.
If <code>port</code> is a string, the message is filtered by <code>e.target.name</code>.
If <code>port</code> is an object, the message is filtered by <code>e.target</code>.

<code>message</code> should be one of:

	'noteoff'
	'noteon'
	'polytouch'
	'cc'
	'pc'
	'channeltouch'
	'pitch'

Functions should return a boolean.