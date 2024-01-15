![[lofi-girl.jpg]]
## Tasks
**Carreer**
- [ ] Use this as your **start-page**, to always keep your most important, current goals with you
- [ ] some important career ToDos [due:: 2024-01-01]
- [ ] learn for exam [due:: 2024-03-01]
- [ ] tasks that are important to you to finish
**Privat**
- [ ] write anything down here [due::18.01.2024]
- [ ] that you have to do [due:: 2024-01-17]
- [ ] in your private life.


| <font style="color:pink">TOP reminders</font> |  | <font style="color:pink">Drink more Water</font> |  | <font style="color:pink">Exercise more</font> |
| ---- | ---- | ---- | ---- | ---- |
## Habits
```dataviewjs

const rawData = await dv.query('TABLE dateformat(Date, "yyyy-MM-dd"), Rating, (Sport * 10) as Sport, (Sleep * 10) as Sleep, (Productive * 10) as Productive FROM "Journal" SORT date asc WHERE Rating and date(Date) < date(now)');

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
            {label: 'Physical Activity',
	            data: rows.map(x => x[3]),
	            backgroundColor: ['pink'],
	            borderColor: ['pink'],
	            borderWidth: ['1'],
		        tension: ['0.3']
	        },
	        {label: 'Productive Time',
		        data: rows.map(x => x[5]),
		        backgroundColor: ['purple'],
		        borderColor: ['purple'],
		        borderWidth: ['1'],
		        tension: ['0.3']
	        }
        ],
    },
}

window.renderChart(chartData, this.container);
```
#### Sport
```dataview
table sum(rows.Sport) as "Sport / Month"
group by dateformat(Date, "yyyy-MM") as Date
where rows.Sport and date(Date) < date(now)
```
```dataview
list "**<font style=\"color:cyan\">" + sum(rows.Sport) + "</font>**"
where Sport and date(Date) < date(now)
group by "=> Total"
```
#### Rating
```dataview
table round(sum(rows.rating) / length(rows.rating),1) as "Avg Monthly Rating"
from "Journal"
where date(Date) < date(now)
group by date(Date).year + "-" + date(Date).month as Date
where rows.date
```
```dataview
list "**<font style=\"color:cyan\">" + round(sum(rows.rating) / length(rows.rating),1) + "</font>**"
from "Journal"
where Rating and date(Date) < date(now)
group by "=> Total"
```
#### Morning Routine
Introduced the morning routine on [[240103 - Morning Routine|08.01.24]]
```dataviewjs

const rawData = await dv.query('TABLE dateformat(Date, "yyyy-MM-dd"), Morning FROM "Journal" SORT date asc WHERE Rating and date(Date) < date(now) and date(Date) > date("2024-01-07")');

const rows = rawData.value.values;

const chartData = {
    type: 'bar',
    tension: '1',
    transparency: '0.75',
    data: {
        labels: rows.map(x => x[1]),
        datasets: [
            {label: 'Morning Routine Successful', data: rows.map(x => x[2]), backgroundColor: ['blue']}
        ],
    },
}

window.renderChart(chartData, this.container);
```
---
![[Life Goals]]

---
#### Data
```dataview
table Rating, Prostrations, Morning
from "Journal"
where Rating and date(Date) < date(now)
```
