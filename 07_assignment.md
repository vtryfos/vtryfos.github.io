---
title: 07_assignment
layout: default
---

# **Web Server Vol 1**   



https://github.com/vtryfos/vtryfos.github.io/assets/143755086/20c5ae85-09fa-49cb-b8de-4ca86d6d1336

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

