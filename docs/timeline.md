---
theme: dashboard
title: Dominant Teams
toc: false
---
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Filterable Bar Plot</title>
  <script src="https://d3js.org/d3.v7.min.js"></script>
</head>

<div class="grid grid-cols-2" style="grid-auto-rows: 504px;">
  <div id="my_dataviz", class="card"></div>
  <div class="card"></div>
</div>

```js
  const data = FileAttachment("data/cbb24.csv").csv({typed: true});
  //console.log(data);
```

```js
  function filterByConference(data, conference) {
    if (conference == "All"){
      return data;
    }
    console.log("Here");
    return data.filter(team => team.CONF === conference);
  }
  const data1 = filterByConference(data, "B10");
  console.log(data1);
```

```js
data.forEach(d => {
  d.BARTHAG = +d.BARTHAG;
  d.W = +d.W;
});

var margin = {top: 10, right: 30, bottom: 30, left: 60},
    width = 460 - margin.left - margin.right,
    height = 400 - margin.top - margin.bottom;

// append the svg object to the body of the page
var svg = d3.select("#my_dataviz")
  .append("svg")
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform",
          "translate(" + margin.left + "," + margin.top + ")");

// Define scales
const x = d3.scaleLinear()
  .domain([0, d3.max(data, d => d.BARTHAG)]).nice()
  .range([0, width]);

const y = d3.scaleLinear()
  .domain([0, d3.max(data, d => d.W)]).nice()
  .range([height, 0]);

// Add X-axis
svg.append("g")
  .attr("transform", "translate(0," + height + ")")
  .call(d3.axisBottom(x));

// Add Y-axis
svg.append("g")
  .call(d3.axisLeft(y));

//Define a tooltip
var tooltip = d3.select("#my_dataviz")
    .append("div")
    .style("opacity", 0)
    .attr("class", "tooltip")
    .style("background-color", "white")
    .style("border", "solid")
    .style("border-width", "1px")
    .style("border-radius", "5px")
    .style("padding", "10px")


var mouseover = function(d) {
  tooltip
    .style("opacity", 1)
}

var mousemove = function(d) {
  var [xCoord, yCoord] = d3.pointer(this);
  tooltip
    .html("School Name: " + d.TEAM)
    .style("left", (xCoord + 90) + "px")
    .style("top", yCoord + "px");
}

// A function that change this tooltip when the leaves a point: just need to set opacity to 0 again
var mouseleave = function(d) {
  tooltip
    .transition()
    .duration(200)
    .style("opacity", 0)
}

// Add data points
svg.selectAll("dot")
  .data(data)
  .enter().append("circle")
  .attr("r", 5)
  .attr("cx", d => x(d.BARTHAG))
  .attr("cy", d => y(d.W))
  .style("fill", "steelblue")
  .on("mouseover", mouseover )
  .on("mousemove", mousemove )
  .on("mouseleave", mouseleave );

// Add labels
svg.append("text")
  .attr("text-anchor", "middle")
  .attr("transform", "translate("+ (width/2) +","+(height+(margin.bottom))+")")
  .text("BARTHAG");

svg.append("text")
  .attr("text-anchor", "middle")
  .attr("transform", "translate("+ (-margin.left/2) +","+(height/2)+")rotate(-90)")
  .text("W");

// Add title
svg.append("text")
  .attr("x", width / 2)
  .attr("y", 0 - (margin.top / 2))
  .attr("text-anchor", "middle")
  .style("font-size", "16px")
  .text("Scatter Plot of BARTHAG vs. W");

// Adjust for responsiveness
svg.attr("preserveAspectRatio", "xMinYMin meet")
  .style("max-width", "100%")
  .style("height", "auto");

// Return the SVG
svg.node();
```
