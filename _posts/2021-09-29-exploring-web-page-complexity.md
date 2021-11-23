---
layout: post
title:  "Exploring web page complexity"
tags: technology
excerpt: "Which popular websites have the most complex HTML code?"
---
As I was preparing content for my web development courses, I wanted to give a comparison point between the complexity of the HTML code we produced in class and the complexity of code (generally not entirely written by humans) found "in the wild".
Not being a person who enjoys counting tags, I developed a little script to assess code complexity.

I am focusing on the following metrics:
- How many HTML elements are there within a page's &lt;body&gt;?
- How many levels deep do these HTML elements go?
- What is the depth of an average element (median depth)?
- How many different tags are used?
- What are the top 3 tags, and how common are they?

The data below was collected on 29 September 2021, using Firefox.
I am logged into some of these websites, so the complexity of the pages depends on the feed being shown at a given time.

| Website | Number of elements | Depth of elements | Number of tag names | Tag #1 | Tag #2 | Tag #3 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [Twitter](https://twitter.com/home) | 1895 | Maximum: 52, Median: 30 | 25 | div (60.4%) | span (15.5%) | path (4.6%) |
| [Reddit](https://www.reddit.com/) | 2705 |  Maximum: 30, Median: 18 | 30 | div (43.7%) | span (16.6%) | i (11.0%) |
| [The Guardian](https://www.theguardian.com/international) | 3592 | Maximum: 21, Median: 13 | 37 | div (28.5%) | span (16.2%) | a (12.2%) |
| [Le Monde](https://www.lemonde.fr/) | 2160 |  Maximum: 14, Median: 7 | 23 | a (23.3%) | span (18.0%) | div (17.7%) |
| [Medium](https://medium.com/) | 1381 |  Maximum: 27, Median: 19 | 15 | div (46.1%) | span (16.5%) | a (9.8%) |
| [BBC](https://www.bbc.com/) | 1170 |  Maximum: 16, Median: 9 | 30 | div (29.7%) | a (22.1%) | li (13.1%) |
| [NOS Nieuws](https://nos.nl/nieuws) | 513 |  Maximum: 16, Median: 11 | 25 | div (14.8%) | li (14.8%) | a (14.2%) |
| [GOV.UK](https://www.gov.uk/) | 371 |  Maximum: 12, Median: 7 | 22 | a (23.5%) | div (19.4%) | li (18.9%) |
| [Informatie van de Rijksoverheid](https://www.rijksoverheid.nl/) | 267 |  Maximum: 13, Median: 7 | 29 | div (22.1%) | a (18.7%) | li (16.1%) |
| [MIT](https://web.mit.edu/) | 366 |  Maximum: 14, Median: 7 | 32 | a (19.1%) | div (17.5%) | path (14.8%) |
| [University of Oxford](https://www.ox.ac.uk/) | 994 |  Maximum: 22, Median: 12 | 23 | div (29.2%) | a (24.2%) | li (22.0%) |
| [Universiteit van Amsterdam](https://www.uva.nl/) | 975 |  Maximum: 13, Median: 5 | 30 | path (15.1%) | div (14.6%) | a (11.3%) |
| [OpenStreetMap](https://www.openstreetmap.org/) | 435 |  Maximum: 10, Median: 7 | 25 | div (46.4%) | a (12.6%) | img (8.7%) |
| [Booking.com](https://www.booking.com/) | 2157 |  Maximum: 19, Median: 9 | 38 | div (23.1%) | span (18.5%) | a (12.4%) |
| [Transport for London](https://tfl.gov.uk/) | 25511 |  Maximum: 25, Median: 8 | 37 | li (35.4%) | br (16.2%) | div (14.0%) |


Some of these websites show interesting things:

- Even though I am using an ad blocker and don't see ads, it seems that the website's business model has a strong influence on the complexity of the website.
Pages with under a thousand elements are non-profit and/or governmental institutions.
- All these websites have **&lt;div&gt;**s in their top 3.
This is unsurprising since this tag is used for grouping content.
For that reason, it is also unsurprising that the websites with the deepest DOM trees are also those who have the highest proportion of **div**.
- I was surprised to see **&lt;path&gt;**, an **SVG** tag, among the top 3 in two websites.
This shows that embedded vector graphics are now becoming very common.
This also means these are websites that use optimization strategies where as much content as possible is loaded at the same time as the HTML, in order to minimize requests and therefore latency.
- I was expecting to see more often **&lt;a&gt;**, the humble anchor tag used for hyperlinks, the heart and soul of the original vision of the World Wide Web as an interconnected library.
It is quite present on news websites, but not so much on social media.
This might directly relate to the fact that social media encourage scrolling feeds, rather than clicking to navigate in a non linear way.
- Why does TfL need more than 9000 **&lt;li&gt;**s?
It turns out that most of them are used for listing the purposes of third-party cookies, and there are about 800 vendors listed in the "Manage partners" screen.

I'm pretty sure there's much more to explore using this method - and the [Digital Methods Initiative] at the University of Amsterdam has many more tools to explore web data.

If you want to explore the complexity of web pages yourself, please find below the JS code I've used today!

```js
let node_names = {},
    node_depths = [],
    top_nodes = [],
    elements_in_body = document.querySelectorAll('body *'),
    element_count = elements_in_body.length;
    
elements_in_body.forEach(function(n) {
    let t = n.tagName.toLowerCase(), e = n, d = 0, k = node_names[t] || 0;
    while (e.tagName !== 'BODY') {
        e = e.parentNode;
        d++;
    }
    while (node_depths.length <= d) {
        node_depths.push(0);
    }
    node_names[t] = k+1;
    node_depths[d]++;
});

let depth_values = node_depths.reduce(function(result, count, depth) { return result.concat(Array(count).fill(depth)) }, []);
let median_depth = ( element_count & 1 )
    ? depth_values[(element_count-1)/2]
    : ((depth_values[element_count/2] + depth_values[element_count/2-1])/2);
for (var k in node_names) {
  top_nodes.push({'name': k, 'count': node_names[k], 'display': k + ' (' + (100*node_names[k]/element_count).toFixed(1) + '%)' });
}
top_nodes.sort(function(a, b) { return b.count - a.count });

console.log(`[${document.title}](${document.location.href}) | ${element_count} |  Maximum: ${node_depths.length}, Median: ${median_depth} | ${top_nodes.length} | ${top_nodes[0].display} | ${top_nodes[1].display} | ${top_nodes[2].display}`);
```
