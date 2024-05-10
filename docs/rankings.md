---
theme: dashboard
title: Predicted Champions
toc: false
---

<!DOCTYPE html>
<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html;charset=utf-8"/ >
		<title>Smoothed D3.js Radar Chart</title>
        <!-- Google fonts -->
		<link href='http://fonts.googleapis.com/css?family=Open+Sans:400,300' rel='stylesheet' type='text/css'>
		<link href='https://fonts.googleapis.com/css?family=Raleway' rel='stylesheet' type='text/css'>
		<!-- D3.js -->
		<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/3.5.6/d3.min.js" charset="utf-8"></script>
		<style>
			body {
				font-family: 'Open Sans', sans-serif;
				font-size: 11px;
				font-weight: 300;
				fill: #242424;
				text-align: center;
				text-shadow: 0 1px 0 #fff, 1px 0 0 #fff, -1px 0 0 #fff, 0 -1px 0 #fff;
				cursor: default;
			}
			.legend {
				font-family: 'Raleway', sans-serif;
				fill: #333333;
			}
			.tooltip {
				fill: #333333;
			}
		</style>
	</head>
	<body>
		<div class="rankings"></div>
		<script src="/components/rankings.js"></script>	
		<script>
      /* Radar chart design created by Nadieh Bremer - VisualCinnamon.com */
			////////////////////////////////////////////////////////////// 
			//////////////////////// Set-Up ////////////////////////////// 
			////////////////////////////////////////////////////////////// 
			var margin = {top: 100, right: 100, bottom: 100, left: 100},
				width = Math.min(700, window.innerWidth - 10) - margin.left - margin.right,
				height = Math.min(width, window.innerHeight - margin.top - margin.bottom - 20);		
			////////////////////////////////////////////////////////////// 
			////////////////////////// Data ////////////////////////////// 
			////////////////////////////////////////////////////////////// 
			var data = [
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 1.25
        },
        { 
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.028901734104046242
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.0847457627118644
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.12048192771084337
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.03164556962025317
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.03773584905660377
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 2
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.625
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 0.20408163265306123
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.029154518950437316
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.038461538461538464
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.12195121951219512
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.029850746268656716
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.04032258064516129
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.12658227848101267
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.04854368932038835
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.02932551319648094
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.10752688172043011
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 2
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.03546099290780142
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.03164556962025317
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.04975124378109453
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.3125
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.028901734104046242
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.03496503496503497
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 1.25
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.032467532467532464
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.034482758620689655
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.25
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.044642857142857144
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 1.1111111111111112
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.029154518950437316
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.2857142857142857
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.09009009009009009
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.036101083032490974
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.03205128205128205
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.06097560975609756
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 2
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.02967359050445104
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.062111801242236024
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 2
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.03389830508474576
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.029585798816568046
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.0546448087431694
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.07142857142857142
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.029154518950437316
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.028328611898016998
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.5263157894736842
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.028901734104046242
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.029239766081871343
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.0425531914893617
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.09900990099009901
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.033112582781456956
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.06622516556291391
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 2
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.045871559633027525
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.04149377593360996
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 2
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 2
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.028985507246376812
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.14084507042253522
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.3333333333333333
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.029850746268656716
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.04
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.05405405405405406
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 0.25
        }
    ],
    [
        {
            "axis": "Adjusted Offensive Efficiency",
            "value": 2
        },
        {
            "axis": "Adjusted Defensive Efficiency",
            "value": 0.028169014084507043
        },
        {
            "axis": "Adjusted Tempo",
            "value": 0.05025125628140704
        },
        {
            "axis": "Effective Field Goal Percentage",
            "value": 0.30303030303030304
        },
        {
            "axis": "Effective Field Goal Percentage Allowed",
            "value": 0.027855153203342618
        },
        {
            "axis": "Turnover Percentage",
            "value": 0.08130081300813008
        },
        {
            "axis": "Turnover Percentage Allowed",
            "value": 0.07246376811594203
        },
        {
            "axis": "Offensive Rebound Percentage",
            "value": 2
        }
    ]
];
			////////////////////////////////////////////////////////////// 
			//////////////////// Draw the Chart ////////////////////////// 
			////////////////////////////////////////////////////////////// 
			var color = d3.scale.ordinal()
				.range([
  "#FF0000", // Red
  "#0000FF", // Blue
  "#00FF00", // Green
  "#FFFF00", // Yellow
  "#800080", // Purple
  "#FFA500", // Orange
  "#00FFFF", // Cyan
  "#FF00FF", // Magenta
  "#008080", // Teal
  "#FFC0CB"  // Pink
]);	
			var radarChartOptions = {
			  w: width,
			  h: height,
			  margin: margin,
			  maxValue: 0.5,
			  levels: 5,
			  roundStrokes: true,
			  color: color
			};
			//Call function to draw the Radar chart
			RadarChart(".rankings", data, radarChartOptions);
		</script>
	</body>
</html>

```js
    (async () => {
        try {
            const getData = await FileAttachment("data/cbbrank.csv").csv({ typed: true });
            const filteredData = getData.filter(entry => {
                return entry.POSTSEASON == 'Champions';
            });
            var myData = [];
            for(let i = 0; i < filteredData.length; i++) {
                myData.push([{axis:"Adjusted Offensive Efficiency", value: 10 / filteredData[i].ADJOE_RK}, 
                {axis:"Adjusted Defensive Efficiency", value: 10 / filteredData[i].ADJDE_RK},
                {axis:"Adjusted Tempo", value: 10 / filteredData[i].ADJ_T_RK},
                {axis:"Effective Field Goal Percentage", value: 10 / filteredData[i].EFG_O_RK},
                {axis:"Effective Field Goal Percentage Allowed", value: 10 / filteredData[i].EFG_D_RK},
                {axis:"Turnover Percentage", value: 10 / filteredData[i].TOR_RK},
                {axis:"Turnover Percentage Allowed", value: 10/ filteredData[i].TORD_RK},
                {axis:"Offensive Rebound Percentage", value: 10 / filteredData[i].ORB_RK},
                ]);
            }
            console.log(myData);
        } catch (error) {
            console.error("Error reading CSV:", error);
        }
    })();
```