<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>真正的御神籤</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: url('./5_工作區域\ 1\ 複本\ 4.jpg') no-repeat center center/cover;
        }
        .container {
            display: grid;
            grid-template-columns: repeat(5, 200px);
            grid-template-rows: repeat(3, 200px);
            gap: 150px;
            width: calc((200px * 5) + (150px * 4));
            height: calc((200px * 3) + (150px * 2));
        }
        .rectangle {
            width: 200px;
            height: 200px;
            background-color: #a6220c;
            border-radius: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 50pt;
            font-weight: bold;
            color: #FFFFFF;
            cursor: pointer;
            transition: transform 0.3s;
            position: relative;
            transform-style: preserve-3d;
        }
        .rectangle:hover {
            transform: scale(1.1);
        }
        .rectangle.flipped {
            transform: rotateY(180deg);
        }
        .front, .back {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            backface-visibility: hidden;
            border-radius: 10px;
        }
        .front {
            background-color: #a6220c;
            color: #FFFFFF;
        }
        .back {
            background-color: #fff2e1;
            color: #a6220c;
            font-size: 36pt;
            text-align: center;
            transform: rotateY(180deg);
            border: 3px solid #a6220c;
        }
    </style>
</head>
<body>
    <div class="container" id="container">
    </div>
    <script>
        let prizes = [
            "系服乙件", "黑色營服乙件", "大容量後背包", "乖乖一包", "乖乖一包",
            "喉糖一條", "喉糖一條", "喉糖一條", "日式紋路色紙", "饕餮紋開瓶器",
            "饕餮紋開瓶器","拉霸機小玩具", "原味奶茶沖泡包", "彈性運動襪", "偵數媒辦法套裝組"
        ];
        
        // 確保獎項分配剛好15個
        while (prizes.length < 15) {
            prizes.push(prizes[Math.floor(Math.random() * prizes.length)]);
        }
        
        // 隨機打亂獎項順序
        prizes.sort(() => Math.random() - 0.5);
        
        const container = document.getElementById('container');
        for (let i = 0; i < 15; i++) {
            const card = document.createElement('div');
            card.classList.add('rectangle');
            card.innerHTML = `
                <div class="front">${i + 1}</div>
                <div class="back">${prizes[i]}</div>
            `;
            card.addEventListener('click', () => {
                card.classList.toggle('flipped');
            });
            container.appendChild(card);
        }
    </script>
</body>
</html>
