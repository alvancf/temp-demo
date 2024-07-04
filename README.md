我想我们已经发现了问题。
在ScrollViewComponentInstance中，我们限制滚动事件的处理，以避免：
向JS端发送过多事件
过于频繁地运行动画更新，而结果并不明显

在第二点上，节流似乎过于激进，可能会导致某些动画出现问题，就像在您的情况下一样。
如果我们不为动画节流事件，结果看起来不错。我们将在今天或明天做出改变。

I  think we've found the issue.
In ScrollViewComponentInstance we throttle processing of scroll events, to avoid:
sending too many events to the JS side
running animation updates too often, when the result would not be noticeable
﻿
It looks like, for that second point, the throttling is too aggressive and may cause issues with some animations, like it does in your case.
If we don't throttle the events for animations, the result looks fine. We'll make that change today or tomorrow.
