---
toc: false
---

<style>

.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-family: var(--sans-serif);
  margin: 4rem 0 8rem;
  text-wrap: balance;
  text-align: center;
}

.hero h1 {
  margin: 2rem 0;
  max-width: none;
  font-size: 14vw;
  font-weight: 900;
  line-height: 1;
  background: linear-gradient(30deg, var(--theme-foreground-focus), currentColor);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero h2 {
  margin: 0;
  max-width: 34em;
  font-size: 20px;
  font-style: initial;
  font-weight: 500;
  line-height: 1.5;
  color: var(--theme-foreground-muted);
}

@media (min-width: 640px) {
  .hero h1 {
    font-size: 90px;
  }
}

p{
  max-width: 800px;
  margin-top: 4;
}

</style>

<div class="hero">
  <h1>Marching Through the Decade</h1>
  <h2>A Statistical Journey of College Basketball (2013-2024)</h2>
  <h3>By: Cole Stewart and Hayden Bentzel</h3>
</div>

<div>
  <h1>Introduction</h1>
  <p>College basketball is a sport that has been around for over a century. It has a rich history and has seen many great players and teams. This project will focus on the last decade of college basketball, from 2013 to 2024. We will look at the top teams, players, and efficiency metrics from this time period. We will also look at the trends and changes that have occurred in the sport over the last decade.</p>
</div>

<div>
  <h1>Research Questions</h1>
  <p>
    <ol>
      <li>What are the top teams in college basketball from 2013 to 2024?</li>
      <li>Who is the most dominant within their conferences?</li>
    </ol>
    We attempted to answer this question by creating a bar chart that dynamically shows the total win leaders in the NCAA over time. The chart is interactive and allows the user to replay the data and see how the rankings change as the years progress. The chart also shows the top teams in each conference and how they compare to each other using an interactable filter where you can choose which conference to analyze.
  </p>
</div>

<div id="observablehq-viewof-replay-230a4197"></div>
<div id="observablehq-viewof-conference-230a4197"></div>
<div id="observablehq-chart-230a4197"></div>
<p>Credit: <a href="https://observablehq.com/d/d72b349146841a86@3162">Bar Chart Race by Data 287 Data Visualization</a></p>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@observablehq/inspector@5/dist/inspector.css">
<script type="module">
import {Runtime, Inspector} from "https://cdn.jsdelivr.net/npm/@observablehq/runtime@5/dist/runtime.js";
import define from "https://api.observablehq.com/d/d72b349146841a86@3162.js?v=4";
new Runtime().module(define, name => {
  if (name === "viewof replay") return new Inspector(document.querySelector("#observablehq-viewof-replay-230a4197"));
  if (name === "viewof conference") return new Inspector(document.querySelector("#observablehq-viewof-conference-230a4197"));
  if (name === "chart") return new Inspector(document.querySelector("#observablehq-chart-230a4197"));
  return ["data","names","datevalues","color","rank","keyframes","bars","nameframes","ticker","prev","next","labels"].includes(name);
});
</script>

<div>
  <h1>Overall Findings</h1>
  <p>
    There are a number of different findings in this visualization that collectively help us answer our research questions. Looking first at the visualization with all conferences selected, we can see that the top teams in college basketball over the last decade are not necessarily from the best conferences. As you can see, schools such as Gonzaga, St. Mary's and Wichita State have been some of the most successful teams in the NCAA over the last decade. This is interesting because these schools are not from the power conferences such as the ACC, Big Ten, or SEC. This shows that success in college basketball is not limited to the power conferences and that schools from smaller conferences can also be successful. Another big finding from this visualization is that the top teams in college basketball have changed over time. Especially at the start of the decade there are a number of teams that are jumping up and down in the standings from year to year. College sports are known for their parity and this visualization shows that this is true in college basketball as well. The top teams in college basketball are constantly changing and there is no one team that has been dominant over the last decade. This is what makes college basketball so exciting and unpredictable. One reason why this is the case is because of the one and done rule in college basketball. This rule allows players to leave college after one year and go to the NBA, and means that teams are constantly losing their best players and have to rebuild every year.
  </p>
  <h1>Design Decisions</h1>
  <p>
    There were a number of different design decisions that we came across while creating this visualization. One of the first issues we encountered was how many teams to include on the graphic. There are a number of conferences that do not have records of all of their teams meaning that the graphic is incomplete when looking at data from smaller conferences. Ultimately, we decided that even when missing data, the best way to show the top teams in the country was to include the top 12 on the graphic. This gave a good idea of the top teams while also including enough information to be able to compare the top teams to some of the lower teams. Another decision was we wanted to include a slider for the years with a play button, but we found it difficult to implement that into D3.js in observable, so we will continue to look into that while we have our current system that plays through the years. The last decision we made was that we originally had the amount of wins by year display which only gave an idea of the top teams in that year, but then we changed it to the aggregate wins so that we could show the top teams throughout this time period and not of a single year.
  </p>
  <h1>Development Process</h1>
  <p>
    The first step of our development process was to dive into Observable and D3.js tutorials to gain a better understanding of the technologies that we would be working with. We learned how to create and deploy a static web page that is accessible via URL. We then looked at D3 Graph Gallery to learn tips and techniques for how to create animated and interactive visualizations. This provided us with a basic understanding of how to create graphs using D3. Next, we gathered information about our dataset and looked at what questions we wanted to answer. When looking at the data, one of the main answers we were looking to find was who are the most dominant teams overall and by conference. After some thoughtful consideration, we decided, what better way than to look at win totals over the last decade. To incorporate animation in the graph, we chose to create a bar chart race that shows how the top team's win totals have changed over time. This was a fun and engaging way to show how college basketball's best teams have performed visually. In order to add interactive features to our visualization we decided that it would be helpful to add a filter-by-conference feature that allows you to look at win totals conference-by-conference. We used an Observable select box to filter the database by the selected conference and then created a new Bar Chart Race with that conference. We used GitHub for version control and collaborated to work on the code together.
  </p>
  <h1>
    Peer Review Questions
  </h1>
  <p>
    <ol>
      <li>What are the strengths of the visualization?</li>
      <li>What are the weaknesses of the visualization?</li>
      <li>What are some potential improvements that could be made to the visualization?</li>
      <li>What are some potential future directions for this project?</li>
    </ol>
  </p>
</div>
