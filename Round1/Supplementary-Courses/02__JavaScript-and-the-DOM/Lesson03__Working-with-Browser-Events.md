If you just wrote a bunch of JavaScript, it would mostly just execute immediately -- as the page is loaded.  But we want to use
JS to enable/enhance interactivity!  This means, we want to write code that will be triggered when certain things
happen --- "things" that we call "events."

We need to know how to monitor events in general, so that we know if/when a specific event occurs.  How
do we do this?  

In Chrome, there is a function called `monitorEvents()` that allows you to see events as they occur.
* [monitorEvents() docs](https://developers.google.com/web/tools/chrome-devtools/console/events#monitor_events)
* to monitor entire document, use cmd+alt+j to open up JS Console in Chrome Developer Tools, then type `monitorEvents(document)`
* to stop monitoring the document: `unmonitorEvents(document)`

### Events I saw while playing around
* click
* dblclick
* mousemove
* pointermove
* pointerover
* pointerout
* mouseout
* mouseleave
* scroll
* resize
* mousewheel

MDN: [List of Events](https://developer.mozilla.org/en-US/docs/Web/Events)


### Side Note: Data Collection
You can imagine that it's monitoring events like this that can help distinguish between a human and a 
bot on the internet.

# The Event Target Interface
Just like we learned that the [Element Interface](https://developer.mozilla.org/en-US/docs/Web/API/Element) 
inherits from the [Node Interface](https://developer.mozilla.org/en-US/docs/Web/API/Node), the Node Interface
inherits from the [EventTarget Interface](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget).

An EventTarget is
> "an interface implemented by objects that can receive events and may have listeners for them.
> Element, document, and window are the most common event targets, but other objects can be event targets too"

The EventTarget is basically the most primitive interface: more primitive than the Node interface.  Any
DOM element (instance of Element, which descends from Node, which descends from EventTarget) and the document object itself (an instance of the [Document Interface](https://developer.mozilla.org/en-US/docs/Web/API/Document),
which descends from the EventTarget interface) can be treated as an event target.  This means that any method
the EventTarget interface has, will be shared by any interface we use (e.g., the document object, a paragraph element, etc):
* EventTarget.addEventListener()
  - Register an event handler of a specific event type on the EventTarget.
* EventTarget.removeEventListener()
  - Removes an event listener from the EventTarget.
* EventTarget.dispatchEvent()
  - Dispatch an event to this EventTarget.
  
## Adding an Event Listener
Listening to an event, listening for an event, responding to an event --- these all mean the same thing in the
JS/DOM world.

Some pseudocode:
```
<event-target>.addEventListener(<event-to-listen-for>, <function-to-run-when-an-event-happens>);
```

That is:
```
target.addEventListener(type, listener);
```

The "target" is the document or element we are interested in (e.g., some <p> element), and the "type" is which
event we are interested in (e.g., "click" or "dblclick").  The "listener" is the function that is triggered when
the event occurs.

Try this out: Go to https://www.google.com and open Chrome Developer Tools (cmd+alt+j):
```js
const search = document.querySelector('#lst-ib');

mainHeading.addEventListener('click', function () {
  alert('You clicked on search!');
});
```

* https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener

---------------------------------

1. Open Chrome
2. Open Developer Tools
3. Traverse the web using code
```js
const google = document.createElement('a');
google.href = 'https://www.google.com'
google.click()
```

-------------------------------------

## Adding an Event Listener to Our Website
<img src="/images/adding-an-event-listener-to-our-website.png" width="500">

Pretty cool!

------------------------

* MDN: [List of Events](https://developer.mozilla.org/en-US/docs/Web/Events)

Read this in a day or two for review:
* MDN: [Introduction to Events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events)


