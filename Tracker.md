### Habits
```dataviewjs
// SETTINGS

const DAYS_TO_SHOW = 21

// SETTINGS END (do not touch after this)

const rawData = await dv.query('TABLE dateformat(Date, "dd.MM - ccc"), (Rating / 10) as Rating, Sleep, Productive, Sport FROM "Journal" SORT date asc WHERE Rating and date(Date) < date(now) and date(Date) > date(now) - dur(' + DAYS_TO_SHOW + ' days)');

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
// SETTINGS

const MEDIUM_RATING = 50
const CURVE_DAMPING = 4
const FACTOR = 2.5

// SETTINGS END (do not touch after this)

const rawData = await dv.query('TABLE dateformat(Date, "yyyy-MM-dd"), Rating SORT date asc WHERE Rating');

const rows = rawData.value.values;

const normalLine = [];
const max = [];
const min = [];
for (i = 0; i < rows.length; i++) {
  normalLine[i] = MEDIUM_RATING;
  max[i] = MEDIUM_RATING + 10;
  min[i] = MEDIUM_RATING - 10;
}

const avg = [];

for (i = 0; i < rows.length; i++) {
	var mi = i - CURVE_DAMPING;
	var ma = i + CURVE_DAMPING;
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
	
	avg[i] = ((avg[i] - MEDIUM_RATING) * FACTOR) + MEDIUM_RATING;
}

const chartData = {
    type: 'line',
    transparency: '0.75',
    data: {
        labels: rows.map(x => x[1]),
        datasets: [
	        {label: 'Averaged',
		        data: avg,
		        backgroundColor: ['cyan'],
		        borderColor: ['cyan'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },
	        {label: 'Exact',
		        data: rows.map(x => x[2]),
		        backgroundColor: ['blue'],
		        borderColor: ['blue'],
		        borderWidth: ['1'],
		        tension: ['0']
	        },
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
