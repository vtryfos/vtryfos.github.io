---
title: 07_assignment
layout: default
---

# **Web Server Vol 1**   

## **Introduction** 
This week’s assignment was to create a web application which hosts a browser based web interface. The web interface’s function is to pull data from the server using HTTP get requests, and then displays these data through a visualization library in the browser. The chosen visualization library for this task was the Chart.js library (For substantial information about this liberty please visit the following link: [Chart.js](https://www.chartjs.org/docs/latest/). Additionally, one of the assignments tasks was to update the chart at least once every 10 seconds. In this case, I chose an update frequency of 1 second. 

## **Installations**
In order to get started with the assignment, there were a plethora of steps to do before starting writing the code, such as installing the VS Code editor in my computer and NodeJS Javascript environment through the command prompt. 

After finishing the NodeJS installation I created a new directory named ‘’Hello’’ (as i couldn't come up with a better name…). Then, I had to install all dependencies in this directory. To navigate into the directory, I used the **npm init** command in the terminal and then the **npm install** command. Lastly, I installed the **express** and **ChartJS** libraries by using the **npm i express** and **npm install chart.js** in the VS Code terminal. 

## **Writing the code**
After a lot of back and forward and some hours spent looking on different webpages, I managed to write the code needed for this assignment. There were in total 3 scripts that were created. The first script created was a .js form script named **serve.js** and was responsible to host the web server. Then, I create a separate folder in the ‘’Hello’’ directory named **public3**. Inside public3, I created two new files, one in .js form and one in .html form named **client.js** and **index .html**, with the first one containing the majority of the coding and functionalities such as creating the randomized data and updating the chart. 
 
Furthermore, this file also contains the tools that are used to visualize the graph (customization). All of those three scripts are given below. Finally, I had to save the scripts and run them through the terminal command **node server.js** in order to be able to see the chart in the browser (Google Chrome).




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
The resulting charts that the code produced are depicted below (Figures 1-3 and Video 1). The main issue I had initially (In Figures 1 and 2) was to update the chart. The **setInterval** function solved this issue, thankfully. Another problem I faced was that the chart was growing in the X-Axis direction as it was updated. To solve this, I decided to remove the very first datapoint of the chart when the length of the datapoint array is equal to 10. This means that as the chart gets updated now the first entry gets removed. The latter results in Figure 3, which is a chart that changes dynamically as time passes (once every second). 

![Screenshot 2023-11-14 004049](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/47327959-c94a-4b3b-a956-f4aceeaa1090)
Figure 1: First iteration of the graph that depicts random values (0-100) in the Y-Axis and the real-time in the X-Axis. Red color line represents the buoy’s vertical displacement in mm while the blue line represents the pendulum’s rotations per minute (RPM).

![Screenshot 2023-11-14 005414](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/9a37a95b-6980-40ec-af07-df7d74ca14c6)
Figure 2: Second iteration of the graph that depicts random values (0-100) in the left hand side Y-Axis as well as random values (0-70) in the right hand Y-Axis and the real-time in the X-Axis. Red color line represents the buoy’s vertical displacement in mm and its values are represented on the right hand Y-Axis while the blue line represents the pendulum’s rotations per minute (RPM) on the left hand side Y-Axis.

![Screenshot 2023-11-14 212529](https://github.com/vtryfos/vtryfos.github.io/assets/143755086/a79fb3ae-3d9d-44e6-a9c4-d31f51c304d0)
Figure 3: Third and final iteration of the graph that depicts random values (0-200) in the left hand side Y-Axis as well as random values (0-100) in the right hand Y-Axis and the real-time in the X-Axis. Here the colors are reversed with respect to the two previous figures as the red color line represents the pendulum’s rotations per minute (RPM) and its values are represented on the right hand Y-Axis while the blue line represents the buoy’s vertical displacement in mm on the left hand side Y-Axis.

https://github.com/vtryfos/vtryfos.github.io/assets/143755086/20c5ae85-09fa-49cb-b8de-4ca86d6d1336

Video 1: Screen capture that depicts the graph’s update every second (Values are similar to figure 3)
