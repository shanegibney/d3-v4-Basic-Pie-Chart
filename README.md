# D3 v4 Basic Pie Chart

Adapted from tutorial on [http://www.cagrimmett.com/](http://www.cagrimmett.com/til/2016/08/19/d3-pie-chart.html)

A simple pie chart.

gh-pages [demo](https://shanegibney.github.io/d3-v4-Basic-Pie-Chart/)

* The first Pie Chart counts the number of each category that exist.

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

* The second Pie Chart sums the value in each category.

```
var category_sum = d3.nest().key(function(d) {
    return d.category;
  })
  .rollup(function(leaves) {
    return d3.sum(leaves, function(d) {
      return d.value;
    });
  }).entries(data)
  .map(function(d) {
    return {
      Category: d.key,
      totalValue: d.value
    };
  });

var category_sum_arcs = d3.pie()
  .value(function(d) {
    return d.totalValue;
  })
  (category_sum);
```

<img width="1242" alt="screen shot 2017-08-30 at 23 51 23" src="https://user-images.githubusercontent.com/17167992/29898574-440a75f0-8dde-11e7-8840-fa37df1bfd72.png">
