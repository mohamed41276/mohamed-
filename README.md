<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>رسم قلوب متحركة ومتكررة</title>
    <style>
        body {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            height: 100vh;
            width: 100vw;
            margin: 0;
            background-color: black;
            color: rgb(253, 4, 4);
            font-family: Arial, sans-serif;
            overflow: hidden;
        }
        .heart-container {
            position: relative;
            width: 200px;
            height: 220px;
            margin: 10px;
        }
        svg {
            width: 100%;
            height: 100%;
        }
        line {
            stroke: red;
            stroke-width: 2;
            stroke-linecap: round;
            opacity: 0;
            transition: transform 1s ease-out, opacity 0.5s;
        }
        .name {
            font-size: 0px;
            font-weight: bold;
            opacity: 0;
            transition: font-size 1s ease-in-out, opacity 1s ease-in-out;
            position: absolute;
            bottom: 0;
            width: 100%;
            text-align: center;
        }
    </style>
</head>
        <h2>mohamed ait ben said </h2>
<body>
    <script>
        function createHeart(index) {
            const container = document.createElement("div");
            container.classList.add("heart-container");
            
            const svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
            svg.setAttribute("viewBox", "-200 -200 400 400");
            svg.id = `heart-svg-${index}`;
            container.appendChild(svg);
            
            const nameElement = document.createElement("div");
            nameElement.classList.add("name");
            nameElement.innerText = "Khadija";
            container.appendChild(nameElement);
            
            document.body.appendChild(container);
            drawHeart(svg, nameElement);
        }
        
        function drawHeart(svg, nameElement) {
            svg.innerHTML = "";
            nameElement.style.fontSize = "0px";
            nameElement.style.opacity = "0";
            
            const scale = 12;
            let delay = 0;
            
            for (let angle = 0; angle < 360; angle += 5) {
                let t = angle * Math.PI / 180;
                let x = scale * (16 * Math.pow(Math.sin(t), 3));
                let y = -scale * (13 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t));
                let line = document.createElementNS("http://www.w3.org/2000/svg", "line");
                line.setAttribute("x1", "0");
                line.setAttribute("y1", "0");
                line.setAttribute("x2", "0");
                line.setAttribute("y2", "0");
                line.style.opacity = "0";
                svg.appendChild(line);
                setTimeout(() => {
                    line.setAttribute("x2", x);
                    line.setAttribute("y2", y);
                    line.style.opacity = "1";
                }, delay);
                delay += 30;
            }
            setTimeout(() => {
                nameElement.style.fontSize = "20px";
                nameElement.style.opacity = "1";
            }, delay);
            
            setTimeout(() => {
                drawHeart(svg, nameElement);
            }, delay + 2000);
        }
        
        function generateHearts(rows, cols) {
            document.body.innerHTML = "";
            for (let i = 0; i < rows * cols; i++) {
                createHeart(i);
            }
        }
        
        generateHearts(3, 4); // إنشاء شبكة من القلوب (3 صفوف × 4 أعمدة)
    </script>
</body>
</html>
