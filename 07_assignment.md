---
title: 07_assignment
layout: default
---

# **Web Server Vol 1**   

## **Introduction**
This week’s assignment was to create a web application which hosts a browser based web interface. The web interface’s function is to pull data from the server using HTTP get requests, and then displays these data through a visualization library in the browser. The chosen visualization library for this task was the Chart.js library (For substantial information about this liberty please visit the following link: Chart.js | Open source HTML5 Charts for your website (chartjs.org). Additionally, one of the assignments tasks was to update the chart at least once every 10 seconds. In this case, I chose an update frequency of 1 second. 

## **Installations**

## **Writing the code**





**Server.js**
```js
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.use(express.static('public3'));

app.get('/data', (req, res) => {
    const randomValue = Math.floor(Math.random() * 200);
    res.json({ value: randomValue });
});



app.listen(port, () => {
    console.log(`Server listening on port ${port}`);
});
```

**Index.html**
```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Real-time Data Visualization</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <canvas id="data-chart" width="700" height="250"></canvas>

    <script src="client.js"></script>
</body>
</html>
```


**Client.js**
```js
document.addEventListener('DOMContentLoaded', () => {
    const ctx = document.getElementById('data-chart').getContext('2d');
    const Vertical_Displacement = [];
    const RPM = [];
    const config = {
        type: 'line',
        data: {
            labels: [],
            datasets: [{
                label: 'Vertical Displacement (mm)',
                data: Vertical_Displacement,
                backgroundColor:'aqua',
                borderColor: 'blue',
                borderWidth: 3,
                fill: false,
            }, {
                label: 'RPM',
                data: RPM,
                backgroundColor:'coral',
                borderColor: 'red',
                borderWidth: 3,
                fill: false,
                yAxisID: 'y-axis-2',
            }],
        },
        options: {
            plugins: {
                legend: {
                    display: true,
                    position: 'top',
                },
                title: {
                    display: true,
                    text: 'Real-Time data measurements',
                },
            },
            animation: {
                duration: 2000,
                easing: 'linear',
            },
            scales: {
                y: {
                    position: 'left',
                    min: 0,
                    max: 200,
                    title: {
                        display: true,
                        color: 'blue',
                        text: 'Vertical Displacement in mm (BLUE)',
                    }, 
                },
                'y-axis-2': {
                    position: 'right',
                    min: 0,
                    max: 100,
                    title: {
                        display: true,
                        color: 'red',
                        text:'RMP (RED)',
                    },
                },
            },
        },
    };
    const chart = new Chart(ctx, config);
    function fetchLiveData() {
        const currentDate = new Date();
        const localTime = currentDate.toLocaleTimeString();
        const datavalue1 = Math.floor(Math.random() * 200) + 1; 
        const datavalue2 = Math.floor(Math.random()* 20) + 1;

        return {
            date: currentDate,
            localTime: localTime,
        values: [datavalue1, datavalue2],
        };
    }
    setInterval(() => {
        const { date, localTime, values } = fetchLiveData();
        Vertical_Displacement.push({ x: date, y: values[0] });
        RPM.push({ x: date, y: values[1] });
        const maxDataPoints = 10;
        if (Vertical_Displacement.length > maxDataPoints) {
            Vertical_Displacement.shift();
            RPM.shift();
            chart.data.labels.shift();
        }
        chart.data.labels.push(localTime);
        chart.data.datasets[0].data = Vertical_Displacement.slice();
        chart.data.datasets[1].data = RPM.slice();
        chart.update();
    }, 1000);
});
```
## **Results**

![Screenshot 2023-11-14 004049](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/47327959-c94a-4b3b-a956-f4aceeaa1090)
Figure 1:

![Screenshot 2023-11-14 005414](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/9a37a95b-6980-40ec-af07-df7d74ca14c6)
Figure 2:

![Screenshot 2023-11-14 212529](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/a79fb3ae-3d9d-44e6-a9c4-d31f51c304d0)
Figure 3:

https://github.com/vtryfos/vtryfos.github.io/assets/143755086/20c5ae85-09fa-49cb-b8de-4ca86d6d1336
