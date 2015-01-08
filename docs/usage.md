---
title: Usage
order: 1
---
#Installation

Either use the npm or bower package managers as per below:

```
bower install mermaid --save-dev
```

```
npm install mermaid --save-dev
```

Or download javascript files:

* [mermaid including dependencies](https://cdn.rawgit.com/knsv/mermaid/0.3.0/dist/mermaid.full.js)

This file bundles mermaid with d3 and dagre-d3.

* [mermaid without dependencies](https://cdn.rawgit.com/knsv/mermaid/0.3.0/dist/mermaid.slim.js)

With this file you will need to include d3 and dagre-d3 yourself.

** Important: **
> It's best to use a specific tag or commit hash in the URL (not a branch). Files are cached permanently after the first request.

Read more about that at [https://rawgit.com/](https://rawgit.com/)

# Usage

Include mermaid on your web page:

```
&lt;script src=&quot;mermaid.full.min.js&quot;&gt;&lt;/script&gt;

```

Further down on your page mermaid will look for tags with ```class="mermaid"```. From these tags mermaid will try to
read the chart definiton which will be replaced with the svg chart.


A chart defined like this:

```
&lt;div class=&quot;mermaid&quot;&gt;
    CHART DEFINITION GOES HERE
&lt;/div&gt;

```

Would end up like this:
```
&lt;div class=&quot;mermaid&quot; id=&quot;mermaidChart0&quot;&gt;
    &lt;svg&gt;
        Chart ends up here
    &lt;/svg&gt;
&lt;/div&gt;

```
An id is also added to mermaid tags without id.

# Example of marked renderer

This is the renderer used for transforming the documentation from markdown to html with mermaid diagrams in the html.

```
    var renderer = new marked.Renderer();
    renderer.code = function (code, language) {
        if(code.match(/^sequenceDiagram/)||code.match(/^graph/)){

            return '&lt;div class="mermaid">'+code+'&gt;/div>';
        }
        else{
            return '&lt;pre>&lt;code>'+code+'&gt;/code>&gt;/pre>';
        }
    };
```