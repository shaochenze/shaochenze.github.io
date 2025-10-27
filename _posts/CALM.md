---
layout: distill
title: Continuous Autoregressive Language Models
description: an in-depth explanation of the paper "Continuous Autoregressive Language Models"
tags: Language Modeling
giscus_comments: true
date: 2021-05-22
featured: true
mermaid:
  enabled: true
  zoomable: true
code_diff: true
map: true
chart:
  chartjs: true
  echarts: true
  vega_lite: true
tikzjax: true
typograms: true


## Equations

This theme supports rendering beautiful math in inline and display modes using [MathJax 3](https://www.mathjax.org/) engine.
You just need to surround your math expression with `$$`, like `$$ E = mc^2 $$`.
If you leave it inside a paragraph, it will produce an inline expression, just like $$ E = mc^2 $$.

In fact, you can also use a single dollar sign `$` to create inline formulas, such as `$ E = mc^2 $`, which will render as $ E = mc^2 $. This approach provides the same effect during TeX-based compilation, but visually it appears slightly less bold compared to double-dollar signs `$$`, making it blend more naturally with surrounding text.

To use display mode, again surround your expression with `$$` and place it as a separate paragraph.
Here is an example:

$$
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

Note that MathJax 3 is [a major re-write of MathJax](https://docs.mathjax.org/en/latest/upgrading/whats-new-3.0.html) that brought a significant improvement to the loading and rendering speed, which is now [on par with KaTeX](http://www.intmath.com/cg5/katex-mathjax-comparison.php).

---

## Citations

Citations are then used in the article body with the `<d-cite>` tag.
The key attribute is a reference to the id provided in the bibliography.
The key attribute can take multiple ids, separated by commas.

The citation is presented inline like this: <d-cite key="gregor2015draw"></d-cite> (a number that displays more information on hover).
If you have an appendix, a bibliography is automatically created and populated in it.

Distill chose a numerical inline citation style to improve readability of citation dense articles and because many of the benefits of longer citations are obviated by displaying more information on hover.
However, we consider it good style to mention author last names if you discuss something at length and it fits into the flow well — the authors are human and it’s nice for them to have the community associate them with their work.

---

## Footnotes

Just wrap the text you would like to show up in a footnote in a `<d-footnote>` tag.
The number of the footnote will be automatically generated.<d-footnote>This will become a hoverable footnote.</d-footnote>

---

## Code Blocks

Syntax highlighting is provided within `<d-code>` tags.
An example of inline code snippets: `<d-code language="html">let x = 10;</d-code>`.
For larger blocks of code, add a `block` attribute:

<d-code block language="javascript">
  var x = 25;
  function(x) {
    return x * x;
  }
</d-code>

**Note:** `<d-code>` blocks do not look good in the dark mode. You can instead use the standard Jekyll syntax highlight with the `highlight` liquid tag.

{% highlight javascript %}
var x = 25;
function(x) {
return x \* x;
}
{% endhighlight %}

You can also write standard Markdown code blocks in triple ticks with a language tag, for instance:

```python
def foo(x):
  return x
```

---

## Interactive Plots

You can add interative plots using plotly + iframes :framed_picture:

<div class="l-page">
  <iframe src="{{ '/assets/plotly/demo.html' | relative_url }}" frameborder='0' scrolling='no' height="500px" width="100%" style="border: 1px dashed grey;"></iframe>
</div>

The plot must be generated separately and saved into an HTML file.
To generate the plot that you see above, you can use the following code snippet:

{% highlight python %}
import pandas as pd
import plotly.express as px
df = pd.read_csv(
'https://raw.githubusercontent.com/plotly/datasets/master/earthquakes-23k.csv'
)
fig = px.density_mapbox(
df,
lat='Latitude',
lon='Longitude',
z='Magnitude',
radius=10,
center=dict(lat=0, lon=180),
zoom=0,
mapbox_style="stamen-terrain",
)
fig.show()
fig.write_html('assets/plotly/demo.html')
{% endhighlight %}

---

## Details boxes

Details boxes are collapsible boxes which hide additional information from the user. They can be added with the `details` liquid tag:

{% details Click here to know more %}
Additional details, where math $$ 2x - 1 $$ and `code` is rendered correctly.
{% enddetails %}

---

## Mermaid

This theme supports creating diagrams directly in markdown using [Mermaid](https://mermaid.js.org/). Mermaid enables users to render flowcharts, sequence diagrams, class diagrams, Gantt charts, and more. Simply embed the diagram syntax within a mermaid code block.

To create a Gantt chart, you can use the following syntax:

````markdown
```mermaid
gantt
    dateFormat  YYYY-MM-DD
    title A Gantt Diagram

    section Section
    Task A           :a1, 2025-01-01, 30d
    Task B           :after a1, 20d
    Task C           :2025-01-10, 12d
```
````

And here’s how it will be rendered:

```mermaid
gantt
    dateFormat  YYYY-MM-DD
    title A Gantt Diagram

    section Section
    Task A           :a1, 2025-01-01, 30d
    Task B           :after a1, 20d
    Task C           :2025-01-10, 12d
```

Similarly, you can also use it to create beautiful class diagrams:

````
```mermaid
classDiagram
direction LR
    class Animal {
        +String species
        +int age
        +makeSound()
    }
    class Dog {
        +String breed
        +bark()
    }
    class Cat {
        +String color
        +meow()
    }
    class Bird {
        +String wingSpan
        +fly()
    }
    class Owner {
        +String name
        +int age
        +adoptAnimal(Animal animal)
    }

    Animal <|-- Dog
    Animal <|-- Cat
    Animal <|-- Bird
    Owner "1" --> "0..*" Animal

    Dog : +fetch()
    Cat : +purr()
    Bird : +sing()
```
````

It will be presented as:

```mermaid
classDiagram
direction LR
    class Animal {
        +String species
        +int age
        +makeSound()
    }
    class Dog {
        +String breed
        +bark()
    }
    class Cat {
        +String color
        +meow()
    }
    class Bird {
        +String wingSpan
        +fly()
    }
    class Owner {
        +String name
        +int age
        +adoptAnimal(Animal animal)
    }

    Animal <|-- Dog
    Animal <|-- Cat
    Animal <|-- Bird
    Owner "1" --> "0..*" Animal

    Dog : +fetch()
    Cat : +purr()
    Bird : +sing()
```

With Mermaid, you can easily add clear and dynamic diagrams to enhance your blog content.

