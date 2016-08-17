---
title:  "jsCodeflow"
subtitle:  "Javascript execution flow visualization"
image: "/images/codeflow.png"
status: "done"
---
It was a very intense experience and coding session too. It was challenging and expentation was high. I'm happy with the outcome of the hackathon and proud to be amongst the finalists.
For a long time I had been thinking about code that draws code. Also I was thinking how tools like backwards debugging ([https://www.youtube.com/watch?v=xpI8hIgOyko](https://www.youtube.com/watch?v=xpI8hIgOyko)) could improve the javascript development experience. So this could focus me on the right track.

So it was clear that my project was going to be productivity and data visualization categories.
The idea was clear: it would draw the execution of javascript code. Also playback control and a timeline would be convenient.

<img src="/images/posts/codeflowvisualizer.png" alt="hi" class="inline"/>
[demo](http://mardie.net/jscodeflowvisualiser/)



Since code execution can be different code execution cannot be inferred from the code. It all depends on the firestarter seed. So I had to record somehow the code execution.

The flow I envisioned was an AST parser being able to inject code into critic parts of the code(constructors, function calls, etc). We can think of events triggered when those nodes where executed. Then a component that executed the modified code and tracks all the triggered ‘events’ and writes a much simpler version of the execution flow. Finally last step is taking the outcome of the former process and visualise in screen. So I had to split the project into 3 sub-projects:

- [EsmorpCodeFlow](https://github.com/mardie/esmorphcodeflow) (This is a modified version of esmorph)
- [JsCodeFlow Reporter](https://github.com/mardie/jscodeflowreporter)
- [JsCodeFlow Visualizer](https://github.com/mardie/jscodeflowvisualiser)


Modified code can be run in any environment (node, browsers, …).
The consistent trackback implementation let us track the execution beyond event loops, event handler and other complex mechanisms.
Visualizer contains some builtin default reports so you don’t need to run any other code if you just want to check how visualization works.
I tried to go the extra mile adding support for ES6(ES 2015) but at this time the only supported feature is ES6 class.

I’m happy with the project even though code could be better but coding in these time limited environment is more experimental and exploratory than any other. Maybe some feature will be added however I think, as an experiment, it’s enough and I prefer investing energy in other projects.
