---
theme: dashboard
title: Conference Comparison
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
<body>

<div id="filter">
  <label for="conference">Select Conference:</label>
  <select id="conference">
    <option value="all">All Conferences</option>
    <option value="B12">Big 12</option>
    <option value="BE">Big East</option>
    <option value="B10">Big Ten</option>
    <option value="SEC">SEC</option>
    <option value="ACC">ACC</option>
    <option value="WCC">WCC</option>
  </select>
</div>

<div id="chart"></div>

  ```js
    const data = FileAttachment("data/cbb24.csv").csv({typed: true});
    console.log(data);
  ```

  ```js
    // Parse CSV 
    drawChart(data);
    function drawChart(data) {
        const margin = {top: 20, right: 30, bottom: 40, left: 100};
        const width = 600 - margin.left - margin.right;
        const height = 400 - margin.top - margin.bottom;

        const svg = d3.select("#chart")
            .append("svg")
            .attr("width", width + margin.left + margin.right)
            .attr("height", height + margin.top + margin.bottom)
            .append("g")
            .attr("transform", `translate(${margin.left},${margin.top})`);

        let allTeams = data.map(d => d.TEAM);

        const x = d3.scaleBand()
            .domain(data.map(d => d.TEAM))
            .range([0, width])
            .padding(0.1);

        const y = d3.scaleLinear()
            .domain([0, d3.max(data, d => parseFloat(d.BARTHAG))])
            .nice()
            .range([height, 0]);

        const xAxis = d3.axisBottom(x);
        const yAxis = d3.axisLeft(y);

        svg.append("g")
            .attr("transform", `translate(0,${height})`)
            .call(xAxis)
            .selectAll("text")
            .style("text-anchor", "end")
            .attr("transform", "rotate(-45)");

        svg.append("g")
            .call(yAxis);

        // Function to update chart based on selected conference
        function update(data) {
            const bars = svg.selectAll(".bar")
                .data(data, d => d.TEAM);

            bars.exit().remove();

            x.domain(data.map(d => d.TEAM));

            // Update x-axis
            svg.select(".x-axis")
                .transition()
                .duration(500)
                .call(xAxis)
                .selectAll("text")
                .style("text-anchor", "end")
                .attr("transform", "rotate(-45)");

            bars.enter().append("rect")
                .attr("class", "bar")
                .attr("x", d => x(d.TEAM))
                .attr("y", height)
                .attr("width", x.bandwidth())
                .attr("height", 0)
                .merge(bars)
                .transition()
                .duration(500)
                .attr("y", d => y(parseFloat(d.BARTHAG)))
                .attr("height", d => height - y(parseFloat(d.BARTHAG)));
        }

        // Initial chart render
        update(data);

        // Filter data based on selected conference
        d3.select("#conference").on("change", function() {
            const selectedConference = this.value;
            let filteredData = data;
            console.log(selectedConference);
            console.log(filteredData);
            if (selectedConference !== "all") {
                filteredData = data.filter(d => d.CONF === selectedConference);
            }
            update(filteredData);
            console.log(filteredData);
        });
    }
  ```

</body>
</html>
