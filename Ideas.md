# Visual Tracking #

## Summary ##
Make oSpyAgent track new and existing windows created by the process it's injected into, and depending on configuration, either do:
  * If the user clicks the left mouse button (could be configurable), starts typing (after not having typed in a while), or connect() is called, log screenshots of all windows belonging to the application.
  * After every WM\_PAINT, log a screenshot of the window where it happened.

## Why ##
Imagine you'd have a TicTacToe game running over for example Windows Live Messenger and you're tracking the protocol with oSpy, you'd play a game through and then stop the trace. Afterwards you'll be looking at a lot of protocol data, and you see roughly what corresponds to the game itself. But then, how do you know what was sent right after you did your first move and placed a cross in (1, 1)? Well, you'd have to note the time when you did it, and manually do a log of what you did when, so you can pinpoint the interesting protocol data afterwards based on timestamps. But what if you could have a snapshots of only the windows taken automatically and logged at the most likely points in time that something happened, and presented with the protocol data? You'd see yourself placing a cross, and right afterwards you'd see send() getting called with some binary protocol data.

## How to present this in oSpy Studio ##
We could have a timeline on the left and tiny thumbnails along the side, a bit like a more interactive version of the visualization feature that oSpy1 had. These thumbnails would be like a deck of cards
\ | /
rotated right by 90 degrees for example, and when you hover one of them, the edges of this one card would glow and the thumbnail slowly turn left (counter-clockwise) until horizontal, while scaling it up a bit.