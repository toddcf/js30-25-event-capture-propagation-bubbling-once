# JavaScript30 #25: Event Capture, Propagation, Bubbling, Once

When you click in the window, the browser first "captures" all of the events going down: the body, the div, the div inside the div, etc.  Nothing is being triggered yet.

When it reaches the bottom, it begins to "bubble" back up, triggering the events as it reaches each level until it gets to the top.

But by adding "capture: true," your function (logText) gets triggered on the capture-down rather than the bubble-up. (By default it would be "capture: false".)

Adding e.stopPropagation() stops it from bubbling up.

Setting "once: true" in this case will listen for a click, and then unbind itself.  This is the equivalent of saying `div.removeEventListener('click', logText);`.  So after the first click, no further clicks will have any effect.  Can be useful in store checkout where you want to prevent users from accidentally placing duplicate orders.