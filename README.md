<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>给最爱的老婆</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            margin: 0;
            padding: 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #333;
            text-align: center;
        }
        
        .container {
            max-width: 800px;
            padding: 30px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        h1 {
            color: #e74c3c;
            margin-bottom: 30px;
            font-size: 2.5rem;
        }
        
        .date-info {
            margin-bottom: 20px;
            font-size: 1.2rem;
            color: #7f8c8d;
        }
        
        .love-message {
            font-size: 1.5rem;
            line-height: 1.6;
            margin: 30px 0;
            padding: 20px;
            background-color: rgba(231, 76, 60, 0.1);
            border-radius: 10px;
            border-left: 5px solid #e74c3c;
        }
        
        .heart-btn {
            width: 80px;
            height: 80px;
            background-color: #e74c3c;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 30px auto;
            cursor: pointer;
            box-shadow: 0 5px 15px rgba(231, 76, 60, 0.4);
            transition: all 0.3s;
            position: relative;
            border: none;
            outline: none;
        }
        
        .heart-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 20px rgba(231, 76, 60, 0.6);
        }
        
        .heart-btn:active {
            transform: scale(0.95);
        }
        
        .heart-btn i {
            color: white;
            font-size: 40px;
        }
        
        .special-event {
            margin-top: 20px;
            padding: 10px;
            background-color: rgba(52, 152, 219, 0.1);
            border-radius: 10px;
            border-left: 5px solid #3498db;
            font-size: 1.2rem;
        }
        
        /* 彩带效果 */
        .confetti {
            position: absolute;
            width: 10px;
            height: 10px;
            background-color: #f00;
            border-radius: 50%;
            pointer-events: none;
        }
        
        .surprise-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            z-index: 100;
            display: none;
            max-width: 80%;
            text-align: center;
            animation: fadeIn 0.5s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translate(-50%, -40%); }
            to { opacity: 1; transform: translate(-50%, -50%); }
        }
        
        .close-surprise {
            position: absolute;
            top: 10px;
            right: 15px;
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
        }
        
        .footer {
            margin-top: 30px;
            color: #7f8c8d;
            font-size: 0.9rem;
        }
        
        /* 心跳动画 */
        @keyframes heartbeat {
            0% { transform: scale(1); }
            25% { transform: scale(1.1); }
            50% { transform: scale(1); }
            75% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .heartbeat {
            animation: heartbeat 1.5s infinite;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
</head>
<body>
    <div class="container">
        <h1>亲爱的老婆 <i class="fas fa-heart" style="color: #e74c3c;"></i></h1>
        
        <div class="date-info">
            <p id="current-date">今天是2023年1月1日，星期X</p>
            <p id="solar-term">节气：XX</p>
            <p id="festival">节日：XX</p>
        </div>
        
        <div class="love-message" id="daily-message">
            今天的情话加载中...
        </div>
        
        <div class="special-event" id="special-message" style="display: none;">
            <!-- 特别节日/节气情话 -->
        </div>
        
        <button class="heart-btn heartbeat" id="heart-btn">
            <i class="fas fa-heart"></i>
        </button>
        
        <div class="footer">
            <p>每一天都比昨天更爱你 ❤️</p>
        </div>
    </div>
    
    <div class="surprise-message" id="surprise-message">
        <span class="close-surprise" id="close-surprise">&times;</span>
        <h2 id="surprise-title">惊喜!</h2>
        <p id="surprise-content">今天也是爱你的一天!</p>
    </div>
    
    <script>
        // 情话库
        const loveMessages = [
            "你知道你和星星有什么区别吗？星星在天上，你在我心里。",
            "我想买一块地，什么地？你的死心塌地。",
            "你知道我的缺点是什么吗？是缺点你。",
            "你猜我想喝什么？我想呵护你。",
            "你知道你和猴子的区别是什么吗？猴子住在树上，你住在我心里。",
            "你知道我为什么感冒了吗？因为我对你没有抵抗力。",
            "你上辈子一定是碳酸饮料吧，为什么我一看到你就能开心的冒泡。",
            "你知道我最大的缺点是什么吗？缺点你。",
            "你知道我想成为什么人吗？你的人。",
            "你知道你和星星的区别吗？星星点亮了黑夜，而你点亮了我的心。",
            "你知道我为什么最近吃素吗？因为你是我的菜。",
            "你知道你和阳光的区别吗？阳光照在身上，你照进心里。",
            "你知道我为什么最近胖了吗？因为你在我心里的分量越来越重了。",
            "你知道你和地图的区别吗？地图上有很多地方，而我的眼里只有你。",
            "你知道你和糖果的区别吗？糖果是甜的，而你比糖果还要甜。",
            "你知道我最近为什么总是发呆吗？因为想你想得入神了。",
            "你知道你和书的区别吗？书可以合上，而我对你的思念却合不上。",
            "你知道我和唐僧的区别吗？唐僧取经，我娶你。",
            "你知道你和手机的区别吗？手机离不开充电器，而我离不开你。",
            "你知道我为什么喜欢笑吗？因为每次想到你，嘴角就不自觉上扬。",
            "你知道你和太阳的区别吗？太阳照耀大地，而你温暖我的心。",
            "你知道我为什么总是迟到吗？因为每次见你都要精心准备很久。",
            "你知道你和雨伞的区别吗？雨伞遮风挡雨，而你遮住了我所有的忧愁。",
            "你知道我为什么总是犯困吗？因为梦里全是你。",
            "你知道你和音乐的区别吗？音乐悦耳，而你悦心。",
            "你知道我为什么喜欢冬天吗？因为可以和你一起取暖。",
            "你知道你和星星的区别吗？星星会眨眼，而你让我的心跳加速。",
            "你知道我为什么喜欢夏天吗？因为可以和你一起吃冰淇淋。",
            "你知道你和花朵的区别吗？花朵会凋谢，而我对你的爱永不凋零。",
            "你知道我为什么喜欢秋天吗？因为可以和你一起看落叶。",
            "你知道你和春天的区别吗？春天带来生机，而你带来心动。",
            "你知道我为什么喜欢晴天吗？因为你的笑容比阳光还灿烂。",
            "你知道你和月亮的区别吗？月亮有阴晴圆缺，而我对你的爱始终如一。",
            "你知道我为什么喜欢雨天吗？因为可以和你共撑一把伞。",
            "你知道你和雪花的区别吗？雪花会融化，而我对你的爱不会。",
            "你知道我为什么喜欢巧克力吗？因为它和你一样甜。",
            "你知道你和咖啡的区别吗？咖啡提神，而你让我神魂颠倒。",
            "你知道我为什么喜欢大海吗？因为对你的爱像海一样深。",
            "你知道你和山的区别吗？山巍峨不动，而我的心为你跳动。",
            "你知道我为什么喜欢星空吗？因为想和你一起数星星。",
            "你知道你和云朵的区别吗？云朵飘忽不定，而我只想停留在你身边。",
            "你知道我为什么喜欢旅行吗？因为想和你一起看世界。",
            "你知道你和风的区别吗？风来去无踪，而我对你的思念无处不在。",
            "你知道我为什么喜欢读书吗？因为想读懂你的心。",
            "你知道你和画的区别吗？画可以欣赏，而你让我想珍藏一生。",
            "你知道我为什么喜欢唱歌吗？因为想唱情歌给你听。",
            "你知道你和电影的区别吗？电影有结局，而我们的故事没有终点。",
            "你知道我为什么喜欢拍照吗？因为想记录有你的每一个瞬间。",
            "你知道你和梦的区别吗？梦会醒，而我对你的爱不会。",
            "你知道我为什么喜欢微笑吗？因为看到你就不自觉笑了。",
            // 可以继续添加更多情话...
        ];
        
        // 节气情话
        const solarTermMessages = {
            "立春": "立春了，万物复苏，而我对你的爱也在不断生长。",
            "雨水": "雨水滋润大地，而你滋润我的心田。",
            "惊蛰": "惊蛰雷动，不如你一笑让我心动。",
            "春分": "春分昼夜平分，而我愿把全部时间都分给你。",
            "清明": "清明时节雨纷纷，而我对你的思念更深沉。",
            "谷雨": "谷雨播种希望，而你播种了我全部的爱。",
            "立夏": "立夏了，天气渐热，而我对你的热情更甚。",
            "小满": "小满未满，而我对你的爱已经满溢。",
            "芒种": "芒种忙种，而我忙着爱你。",
            "夏至": "夏至日最长，而我对你的思念更长。",
            "小暑": "小暑炎热，而我对你的爱更热烈。",
            "大暑": "大暑最热，而你是我最热的爱恋。",
            "立秋": "立秋了，暑气渐消，而我对你的爱丝毫不减。",
            "处暑": "处暑暑气止，而我对你的爱永不止息。",
            "白露": "白露凝霜，而我的心里装满了你。",
            "秋分": "秋分昼夜均，而我愿与你平分秋色。",
            "寒露": "寒露渐冷，而你的温暖让我心热。",
            "霜降": "霜降天寒，而你的拥抱最温暖。",
            "立冬": "立冬了，万物收藏，而我想把你收藏在心里。",
            "小雪": "小雪飘飘，而我对你的爱纷纷扬扬。",
            "大雪": "大雪纷飞，而我对你的爱铺天盖地。",
            "冬至": "冬至夜最长，而我对你的思念更长。",
            "小寒": "小寒冷冽，而你的笑容最温暖。",
            "大寒": "大寒最冷，而你是我最暖的依靠。"
        };
        
        // 节日情话
        const festivalMessages = {
            "元旦": "新年第一天，第一个想到的就是你，元旦快乐我的爱！",
            "情人节": "情人节快乐！你是我今生唯一的情人，也是永远的挚爱。",
            "妇女节": "女神节快乐！在我心中你永远是最美的女神。",
            "劳动节": "劳动节快乐！感谢你为这个家付出的一切，辛苦了亲爱的。",
            "儿童节": "儿童节快乐我的小宝贝！在我心里你永远是需要我呵护的小朋友。",
            "七夕": "七夕快乐！牛郎织女一年一见，而我们天天相见更幸福。",
            "中秋节": "中秋月圆人团圆，而我最想团圆的人就是你。",
            "国庆节": "国庆节快乐！和你在一起的每一天都值得庆祝。",
            "圣诞节": "圣诞快乐！你就是我今年最想要的礼物。",
            "生日": "生日快乐我的爱！你出生的那天就是我最感恩的日子。",
            "结婚纪念日": "结婚纪念日快乐！每一天都比昨天更爱你。",
            "相识纪念日": "还记得我们相识的那天吗？那是我生命中最美好的一天。"
        };
        
        // 获取当前日期信息
        function getCurrentDate() {
            const now = new Date();
            const year = now.getFullYear();
            const month = now.getMonth() + 1;
            const day = now.getDate();
            const weekdays = ["日", "一", "二", "三", "四", "五", "六"];
            const weekday = weekdays[now.getDay()];
            
            return {
                year,
                month,
                day,
                weekday,
                dateStr: `${year}年${month}月${day}日，星期${weekday}`,
                dayOfYear: Math.floor((now - new Date(year, 0, 0)) / (1000 * 60 * 60 * 24))
            };
        }
        
        // 获取节气信息（简化版，实际节气计算复杂）
        function getSolarTerm(date) {
            // 这里是一个简化的节气判断，实际节气计算需要精确的天文计算
            const terms = [
                {name: "小寒", month: 1, day: 5},
                {name: "大寒", month: 1, day: 20},
                {name: "立春", month: 2, day: 4},
                {name: "雨水", month: 2, day: 19},
                {name: "惊蛰", month: 3, day: 5},
                {name: "春分", month: 3, day: 20},
                {name: "清明", month: 4, day: 4},
                {name: "谷雨", month: 4, day: 20},
                {name: "立夏", month: 5, day: 5},
                {name: "小满", month: 5, day: 21},
                {name: "芒种", month: 6, day: 6},
                {name: "夏至", month: 6, day: 21},
                {name: "小暑", month: 7, day: 7},
                {name: "大暑", month: 7, day: 23},
                {name: "立秋", month: 8, day: 7},
                {name: "处暑", month: 8, day: 23},
                {name: "白露", month: 9, day: 7},
                {name: "秋分", month: 9, day: 23},
                {name: "寒露", month: 10, day: 8},
                {name: "霜降", month: 10, day: 23},
                {name: "立冬", month: 11, day: 7},
                {name: "小雪", month: 11, day: 22},
                {name: "大雪", month: 12, day: 7},
                {name: "冬至", month: 12, day: 22}
            ];
            
            for (const term of terms) {
                if (date.month === term.month && date.day === term.day) {
                    return term.name;
                }
            }
            
            return null;
        }
        
        // 获取节日信息（简化版）
        function getFestival(date) {
            const festivals = [
                {name: "元旦", month: 1, day: 1},
                {name: "情人节", month: 2, day: 14},
                {name: "妇女节", month: 3, day: 8},
                {name: "劳动节", month: 5, day: 1},
                {name: "儿童节", month: 6, day: 1},
                {name: "七夕", month: 8, day: 25}, // 七夕日期每年不同，这里简化
                {name: "中秋节", month: 9, day: 21}, // 中秋节日期每年不同，这里简化
                {name: "国庆节", month: 10, day: 1},
                {name: "圣诞节", month: 12, day: 25}
            ];
            
            for (const festival of festivals) {
                if (date.month === festival.month && date.day === festival.day) {
                    return festival.name;
                }
            }
            
            return null;
        }
        
        // 获取每日情话（基于日期确保每天不同）
        function getDailyLoveMessage(date) {
            // 使用日期作为种子确保每天相同
            const seed = date.year * 10000 + date.month * 100 + date.day;
            const index = seed % loveMessages.length;
            return loveMessages[index];
        }
        
        // 创建彩带效果
        function createConfetti() {
            const colors = ['#e74c3c', '#3498db', '#2ecc71', '#f1c40f', '#9b59b6', '#1abc9c'];
            
            for (let i = 0; i < 100; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = -10 + 'px';
                confetti.style.width = Math.random() * 10 + 5 + 'px';
                confetti.style.height = Math.random() * 10 + 5 + 'px';
                
                document.body.appendChild(confetti);
                
                // 动画
                const animation = confetti.animate([
                    { top: '-10px', opacity: 1, transform: 'rotate(0deg)' },
                    { top: '100vh', opacity: 0, transform: 'rotate(' + (Math.random() * 360) + 'deg)' }
                ], {
                    duration: Math.random() * 3000 + 2000,
                    easing: 'cubic-bezier(0.1, 0.8, 0.3, 1)'
                });
                
                animation.onfinish = () => {
                    confetti.remove();
                };
            }
        }
        
        // 显示惊喜消息
        function showSurpriseMessage() {
            const surpriseMessages = [
                "你是我的今天和所有的明天",
                "遇见你是我这辈子最幸运的事",
                "我想和你一起慢慢变老",
                "你是我生命中最美的风景",
                "有你的地方就是家",
                "爱你是我做过最正确的事",
                "你是我每天早上醒来的理由",
                "我的世界因你而完整",
                "你是我今生唯一的挚爱",
                "和你在一起的每一秒都值得珍惜"
            ];
            
            const randomMessage = surpriseMessages[Math.floor(Math.random() * surpriseMessages.length)];
            document.getElementById('surprise-content').textContent = randomMessage;
            document.getElementById('surprise-message').style.display = 'block';
        }
        
        // 初始化页面
        function initPage() {
            const date = getCurrentDate();
            
            // 显示日期信息
            document.getElementById('current-date').textContent = date.dateStr;
            
            // 获取并显示节气
            const solarTerm = getSolarTerm(date);
            if (solarTerm) {
                document.getElementById('solar-term').textContent = `节气：${solarTerm}`;
                document.getElementById('special-message').textContent = solarTermMessages[solarTerm];
                document.getElementById('special-message').style.display = 'block';
            } else {
                document.getElementById('solar-term').textContent = '';
            }
            
            // 获取并显示节日
            const festival = getFestival(date);
            if (festival) {
                document.getElementById('festival').textContent = `节日：${festival}`;
                if (!solarTerm) { // 如果当天不是节气才显示节日情话
                    document.getElementById('special-message').textContent = festivalMessages[festival];
                    document.getElementById('special-message').style.display = 'block';
                }
            } else {
                document.getElementById('festival').textContent = '';
            }
            
            // 显示每日情话
            document.getElementById('daily-message').textContent = getDailyLoveMessage(date);
            
            // 爱心按钮事件
            document.getElementById('heart-btn').addEventListener('click', function() {
                createConfetti();
                showSurpriseMessage();
            });
            
            // 关闭惊喜消息
            document.getElementById('close-surprise').addEventListener('click', function() {
                document.getElementById('surprise-message').style.display = 'none';
            });
        }
        
        // 页面加载完成后初始化
        window.addEventListener('DOMContentLoaded', initPage);
    </script>
</body>
</html>
```
