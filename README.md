# Overview

If you want to get a [CodeMirror 6](https://codemirror.net/) editor up and running but aren't sure how to start, this repo is for you. Maybe you've even used CodeMirror 5 in the past and you feel like by comparison CodeMirror 6 just dumps a bunch of legos at your feet with minimal instructions and tells you to build your own editor. If that's you, fear not! I've crafted some examples to get you tinkering and iterating in no time.

# Quickstart

The quickest way to get CodeMirror 6 up and running is to just grab a copy of the `dist/cm6.bundle.js` file I've created to include in your own HTML.

Here's a minimal example HTML page that uses it: 

[Example 1](https://rpgillespie6.github.io/codemirror-quickstart/examples/example1.html)

Here's a slightly more complex example that lets you choose the editor theme on the fly:

[Example 2](https://rpgillespie6.github.io/codemirror-quickstart/examples/example2.html)

Here's an example that illustrates how states and views work together:

[Example 3](https://rpgillespie6.github.io/codemirror-quickstart/examples/example3.html)

You can also run these examples locally by cloning this repository and running `python3 -m http.server 8000` (or any webserver) from the root of the repository and then navigating to i.e. http://localhost:8000/examples/example1.html.

Note that `cm6.bundle.js` does not contain every possible extension of CodeMirror 6 - just the main ones and a few I personally like to use. If you want syntax highlighting for a language other than javascript or a different theme or some other extension not included here, you'll have to create your own custom bundle.

# How to Create Your Own Custom Bundle

So you've tinkered with the examples, and now you want to create your own custom-tailored `cm6.bundle.js` that meets your needs. Why would you want to create your own custom-tailored bundle? Well, for one thing it'll likely be smaller on disk than the monolithic one provided here. But also, maybe you need python syntax highlighting instead of javascript. That's the real beauty of CodeMirror 6 - it's super modular design allows you to generate an editor with only the features you want and nothing else; no bloating your web page with extra code that you aren't using!

The official docs mention how to create a bundle [here](https://codemirror.net/examples/bundle/) but it doesn't do much handholding.

So this section will walk you through exactly how I created the `cm6.bundle.js` in this repo and then show you how to make tweaks.

1. Install npm packages `rollup` and `@rollup/plugin-node-resolve`

2. Install CodeMirror 6 npm packages that you want (for example: `@codemirror/lang-python` if you want python support)

You can simply run `npm install` in the root of this repo which will install all the dependencies currently used by `dist/cm6.bundle.js` as well as `rollup` and `minify`.

Using [src/editor.js](src/editor.js) as a template, delete extensions, add different extensions, etc.

Create bundle with: `npx rollup src/editor.js -f iife -o dist/cm6.bundle.js -p @rollup/plugin-node-resolve --output.name cm6`

(Optional) Minify bundle with: `cd dist && npx minify cm6.bundle.js > cm6.bundle.min.js`

If you are doing these steps a lot as you iterate, you can use a program to watch your `editor.js` for changes and autogenerate the bundle. I personally use [reflex](https://github.com/cespare/reflex) but there are npm packages that do the same. The reflex command I used to develop `cm6.bundle.js` in this repo is found in [scripts/watch_and_bundle.sh](scripts/watch_and_bundle.sh)