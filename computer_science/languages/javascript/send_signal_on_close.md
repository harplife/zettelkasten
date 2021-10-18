---
aliases: [How to send a signal when a page closes]
tags: [javascript, code, example, how-to, work]
status: ongoing
edited: 2021-10-18
---

# How to send a signal when a page closes
A code example for [[javascript|JavaScript]].
This is also a valid web server security implementation #todo .

This came up when dealing with GS (Good Software) Certification #todo at work.
We had to implement a function that keeps track of people logging out via closing the tab or the browser.

Luckily, Chrome supports both `beforeunload` and `sendBeacon` (so far).

```javascript
window.addEventListener("beforeunload", function (e) {
  navigator.sendBeacon('/log', 'session closed');
});
```

I tested it with a [[python|Python]] Flask web server.

A POST API at `/log` must be open to receive a `DOMString`, like so.
```python
@app.route("/log", methods=['POST'])
def get_log():
    data = request.data.decode('utf-8')
    print(data) # prints 'session closed'
```

In order to logout an account, the webserver should receive a session ID and handle it from there.
It hasn't been tested yet (I'm wainting on Seo Seonim to implement it with Java).

Considering Flask has modules for dealing with login, I do wonder:
1. Can Flask detect logging out #todo
2. How to implement Logout Tracking with Flask #todo

## References
- [sendBeacon](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/sendBeacon)
- [beforeunload event](https://developer.mozilla.org/en-US/docs/Web/API/Window/beforeunload_event)