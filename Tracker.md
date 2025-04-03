### Habits
```dataviewjs

const rawData = await dv.query('TABLE dateformat(Date, "dd.MM - ccc"), (((Rating / 10) * 3) - 13) as Rating, (Prostrations / 27) as Prostrations, Sleep, Productive, Sport FROM "Journal" SORT date asc WHERE Rating and date(Date) < date(now) and date(Date) > date(now) - dur(21 days)');

const rows = rawData.value.values;

const chartData = {
    type: 'line',
    transparency: '0.75',
    data: {
        labels: rows.map(x => x[1]),
        datasets: [
            {label: 'Rating',
	            data: rows.map(x => x[2]),
	            backgroundColor: ['cyan'],
	            borderColor: ['cyan'],
	            borderWidth: ['1'],
	            tension: ['0.3']
	        },
	        {label: 'Sleep',
		        data: rows.map(x => x[4]),
		        backgroundColor: ['blue'],
		        borderColor: ['blue'],
		        borderWidth: ['1'],
		        tension: ['0.3']
		    },
	        {label: 'Productive',
		        data: rows.map(x => x[5]),
		        backgroundColor: ['purple'],
		        borderColor: ['purple'],
		        borderWidth: ['1'],
		        tension: ['0.3']
	        },
	        {label: 'Sport',
		        data: rows.map(x => x[6]),
		        backgroundColor: ['green'],
		        borderColor: ['green'],
		        borderWidth: ['1'],
		        tension: ['0.3']
	        }
        ],
    },
}

window.renderChart(chartData, this.container);
```
### Rating Overall
```dataviewjs
const rawData = await dv.query('TABLE dateformat(Date, "yyyy-MM-dd"), Rating SORT date asc WHERE Rating');

const rows = rawData.value.values;

const normalLine = [];
const max = [];
const min = [];
for (i = 1; i < rows.length; i++) {
  normalLine[i] = 60;
  max[i] = 70;
  min[i] = 50;
}

const avg = [];
const avgrange = 4;
const factor = 2.5;
for (i = 1; i < rows.length; i++) {
	var mi = i - avgrange;
	var ma = i + avgrange;
	if (mi < 0) mi = 0;
	if (ma >= rows.length) ma = rows.length - 1;
	
	var values = 0;
	var count = 0;
	for (k = mi; k <= ma; k++) {
		var weight = 1 / Math.pow(1.4,Math.abs(i-k));
		values += rows[k][2] * weight;
		count += weight;
	}
	avg[i] = values / count;
	
	avg[i] = ((avg[i] - 60) * factor) + 60;
}

const chartData = {
    type: 'line',
    transparency: '0.75',
    data: {
        labels: rows.map(x => x[1]),
        datasets: [
	        {label: 'Rating',
		        data: rows.map(x => x[2]),
		        backgroundColor: ['cyan'],
		        borderColor: ['cyan'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },
	        {label: 'Averaged',
		        data: avg,
		        backgroundColor: ['blue'],
		        borderColor: ['blue'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },/*
	        {label: 'Max Normal',
		        data: max,
		        backgroundColor: ['green'],
		        borderColor: ['green'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },
	        {label: 'Min Normal',
		        data: min,
		        backgroundColor: ['green'],
		        borderColor: ['green'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },*/
	        {label: 'Normal',
		        data: normalLine,
		        backgroundColor: ['darkgreen'],
		        borderColor: ['darkgreen'],
		        borderWidth: ['0'],
		        tension: ['0']
	        }
        ],
    },
}

window.renderChart(chartData, this.container);
```

```dataview
list "**<font style=\"color:cyan\">" + round(sum(rows.rating) / length(rows.rating),1) + "</font>**"
FROM "Journal"
WHERE Rating
GROUP BY "=> Average Rating"
```

### Top 10 Days

```dataviewjs

const rawData = await dv.query('TABLE dateformat(Date, "yyyy-MM-dd"), Rating SORT Rating desc WHERE Rating');

const rows = rawData.value.values;

const chartData = {
    type: 'line',
    transparency: '0.75',
    data: {
        labels: rows.map(x => x[1]),
        datasets: [
	        {label: 'Rating',
		        data: rows.map(x => x[2]),
		        backgroundColor: ['cyan'],
		        borderColor: ['cyan'],
		        borderWidth: ['1'],
		        tension: ['0']
	        }
        ],
    },
}

//window.renderChart(chartData, this.container);

//dv.paragraph("|**Day**|" + rows[0][1] + "|\n|-|-|\n|**Rating ->**|**<font style=\"color:orange\">" + rows[0][2] + "%</font>**|");

var result = "| Rating | Day | Title |\n|-|-|-|\n";
for (i = 0; i < 10 && i < rows.length; i++) {
  result += "|**<font style=\"color:orange\">"
			  + rows[i][2] + "%</font>**|**"
			  + rows[i][1] + "**|"
			  + rows[i][0] + "|\n"
}

dv.paragraph(result);
```
