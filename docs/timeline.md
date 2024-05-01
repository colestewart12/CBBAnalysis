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

<div id="observablehq-chart-bcbc1baa"></div>
<p>Credit: <a href="https://observablehq.com/d/d72b349146841a86@3090">Bar Chart Race by Data 287 Data Visualization</a></p>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@observablehq/inspector@5/dist/inspector.css">
<script type="module">
import {Runtime, Inspector} from "https://cdn.jsdelivr.net/npm/@observablehq/runtime@5/dist/runtime.js";
import define from "https://api.observablehq.com/d/d72b349146841a86@3090.js?v=4";
new Runtime().module(define, name => {
  if (name === "chart") return new Inspector(document.querySelector("#observablehq-chart-bcbc1baa"));
});
</script>