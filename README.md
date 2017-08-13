# D3 v4 Basic Pie Chart

A simple pie chart

Count number of each category tat exist.

```
var category_count = d3.nest()
  .key(function(d) {
    return d.category;
  })
  .rollup(function(leaves) {
    return leaves.length;
  })
  .entries(data);

var category_arcs = d3.pie()
  .value(function(d) {
    return d.value;
  })
  (category_count);
```

gh-pages [demo](https://shanegibney.github.io/d3-v4-Basic-Pie-Chart/)

<img width="291" alt="screen shot 2017-08-13 at 13 22 03" src="https://user-images.githubusercontent.com/17167992/29249584-73cb1e1e-802a-11e7-9fa5-030e4e28e22a.png">
