# Espresso Bar Slot Machine

## Intro
Here's a simple slot machine that gives out a drink when the slots match up with
the appropriate device, filter, and ingredient. The possible drinks are: coffee,
tea, and espresso.

## Files To Look At
The CSS file(s) were auto-generated. I also included the Sass source map generated,
for debugging purposes.

## Third-Party Frameworks/libraries Used
* [AngularJS](http://angularjs.org) - for JS magic (also I wanted to try it out)
* [Sass](http://sass-lang.com) - for fast CSS writing
* [normalize.css](http://necolas.github.io/normalize.css/) - for defining basic cross-browser styles (the Sass version is used here)
* [Bourbon](http://bourbon.io/) - for vendor prefix mixins

## Notes

### Use of AngularJS
This is my first time using AngularJS. I thought I would try it out. Turned out
to be cooler than I thought would be.

### The machine's appearance
I thought a lot about how the machine would look. I figured it would look like
one of those super-convenient coffee machines like the Nespresso, except wider
and has a little cubby where a drink magically appears.

Everything except the button is hand-drawn. I *could* fuss around with CSS to
draw the machine, but that would take forever. I *could* take images off the
internet to make my sprites, but that wouldn't be very original.

### Fixed-width versus fluid-width
I *really* wanted to make this machine fluid-width, so it could fit different
screen sizes. In fact, I almost did.

The trouble arose with the background-positioning. The sprites could adjust in
size with the use of `background-size`, but scrolling and setting makes use of
pixels, which doesn't mix well with `background-size`. While `background-position`
can also take percentage values, values exceeding 100% start positioning from the
bottom/right of an element, and thus work differently than how the 0-100% range
works.

Viewport values (vw, vh, etc.) could work, but they'd require quite a bit of
tweaking.

### Espresso grounds versus coffee grounds
They don't really look that different in real-life, so I added whole beans to
the espresso grounds for distinguishing purposes.

### Slot timing
Currently, the machine works like this:
1. Start the slots, and set the output drink three seconds later.
2. Meanwhile, the slots spin for two seconds.

This assumes that everything starts and stops as expected, but ideally, step 1
would be "Start the slots, and *listen for the slots to return something*". I
ran out of time to figure this out.

### Passing $interval and $timeout to the Slot object
For data binding to work, I had to pass in `$interval` and `$timeout` to
`Slot.animateSlot()`. I suppose I can avoid this by changing the Slot object to
a Slot module. Need to learn how to do that...

### Slot object parameters
Ideally the Slot object would also take slot speed, height, and some other parameters
for robustness.
