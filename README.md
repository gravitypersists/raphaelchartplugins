This is a simple charting plugin library I made for building interactive SVG graphs using the Raphael.js library.

Feel free to use or modify as you please.



To create a simple column chart:

```javascript
// create a Raphael paper object like you normally would
var width = 500, height = 500;
var paper = Raphael(element, width, height);

// use the chart plugin to create a chart, this one has a margin of 100 pixels
var xRange = [0,5], 
    yRange = [0,10];
var chart = paper.chart([100,100], [width-100,height-100], xRange, yRange);

// draw a y-axis with some labels and ticks
var yaxis = chart.addVerticalAxis([0,10])
for (var i=2; i<=10; i=i+2) {
    yaxis.addTick(i);
    yaxis.addLabel(i, i);
    chart.addHorizontalLine(i).attr({stroke:"#ccc", "stroke-dasharray":"- "})
}

// draw an x-axis
var xaxis = chart.addHorizontalAxis([0,5]);

// draw a set of columns from a dataset
var data = {"Cats":4, "Dogs":7, "Birds":2, "Reptiles":1};
var i=0;
for (var x in data) {
    i++;
    chart.addColumn(i, data[x], {animationSpeed:400, width:20}).attr({"fill":"red"});
    xaxis.addLabel(i, x);
}
```

the result of the above code:

![Simple column chart](https://raw.github.com/gitpullgravity/raphaelchartplugins/master/samples/simple_chart_screenshot.png)