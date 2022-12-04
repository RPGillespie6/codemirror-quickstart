# Overview

This repo is for you if you want to get a [CodeMirror 6](https://codemirror.net/) editor up and running but aren't sure how to start. Maybe you've even used CodeMirror 5 in the past and you feel like by comparison CodeMirror 6 just dumps a bunch of legos at your feet without instructions and tells you to build your own editor. If that's you, fear not! I've crafted some examples to get you tinkering and interating in no time.

# Quickstart

The quickest way to get CodeMirror 6 up and running is to just grab a copy of the `dist/cm6.bundle.js` file I've created to include in your own HTML.

Here's a minimal example HTML page that uses it: 

[Example 1](https://rpgillespie6.github.io/codemirror-quickstart/examples/example1.html)

Here's a slightly more complex example that lets you generate an editor with just the features you want on the fly:

[Example 2](https://rpgillespie6.github.io/codemirror-quickstart/examples/example2.html)

Here's an example that illustrates the difference between States and Views (note how ctrl-z undo history is tied to the state, not the view!):

[Example 2](https://rpgillespie6.github.io/codemirror-quickstart/examples/example3.html)

You can also run these examples locally by cloning this repository and running `python3 -m http.server 8000` (or any webserver) from the root of the repository and then navigating to i.e. http://localhost:8000/examples/example1.html.

Note that `cm6.bundle.js` does not contain every possible extension of CodeMirror 6 - just the main ones and a few I personally like to use. If you want syntax highlighting for a language other than javascript or a different theme or some other extension not included here, you'll have to create your own custom bundle.

# How to Create Your Own Custom Bundle

So you've tinkered with the examples, and now you want to create your own custom-tailored `cm6.bundle.js` that meets your needs. Why would you want to create your own custom-tailored `cm6.bundle.js`? Well, for one thing it'll likely be smaller on disk than the monolithic one provided here. But also, maybe you need python syntax highlighting instead of javascript. That's the real beauty of CodeMirror 6 - it's super modular design allows you to generate an editor with only the features you want and nothing else; no bloating your web page with extra code that you aren't using!

The official docs mention how to create a bundle [here](https://codemirror.net/examples/bundle/) but it doesn't do much handholding.

So this section will walk you through exactly how I created the `cm6.bundle.js` in this repo and then show you how to make tweaks.

