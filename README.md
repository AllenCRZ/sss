
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>给最爱的老婆</title>
    <style>
        * {
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
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
            -webkit-text-size-adjust: 100%;
            touch-action: manipulation;
        }
        
        .container {
            width: 92%;
            max-width: 500px;
            padding: 20px;
            margin: 20px auto;
            background-color: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
            word-break: break-word;
        }
        
        h1 {
            color: #e74c3c;
            margin: 15px 0;
            font-size: 1.8rem;
            font-weight: 600;
        }
        
        .date-info {
            margin-bottom: 15px;
            font-size: 1rem;
            color: #7f8c8d;
            line-height: 1.5;
        }
        
        .love-message {
            font-size: 1.2rem;
            line-height: 1.6;
            margin: 20px 0;
            padding: 15px;
            background-color: rgba(231, 76, 60, 0.1);
            border-radius: 10px;
            border-left: 4px solid #e74c3c;
        }
        
        .heart-btn {
            width: 70px;
            height: 70px;
            background-color: #e74c3c;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 20px auto;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(231, 76, 60, 0.4);
            transition: all 0.3s;
            position: relative;
            border: none;
            outline: none;
            -webkit-user-select: none;
            user-select: none;
        }
        
        .heart-btn:active {
            transform: scale(0.95);
        }
        
        .heart-btn i {
            color: white;
            font-size: 35px;
        }
        
        .special-event {
            margin-top: 15px;
            padding: 10px;
            background-color: rgba(52, 152, 219, 0.1);
            border-radius: 8px;
            border-left: 4px solid #3498db;
            font-size: 1.1rem;
            line-height: 1.5;
        }
        
        /* 彩带效果 */
        .confetti {
            position: fixed;
            width: 8px;
            height: 8px;
            background-color: #f00;
            border-radius: 50%;
            pointer-events: none;
            z-index: 999;
        }
        
        .surprise-message {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: rgba(255, 255, 255, 0.98);
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
            z-index: 1000;
            display: none;
            width: 85%;
            max-width: 350px;
            text-align: center;
            animation: fadeIn 0.3s;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translate(-50%, -45%); }
            to { opacity: 1; transform: translate(-50%, -50%); }
        }
        
        .close-surprise {
            position: absolute;
            top: 8px;
            right: 12px;
            font-size: 20px;
            cursor: pointer;
            color: #7f8c8d;
            padding: 5px;
        }
        
        .footer {
            margin-top: 20px;
            color: #7f8c8d;
            font-size: 0.85rem;
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
        
        /* 微信浏览器适配 */
        @media (max-width: 480px) {
            .container {
                padding: 15px;
                width: 90%;
            }
            
            h1 {
                font-size: 1.6rem;
                margin: 10px 0;
            }
            
            .love-message {
                font-size: 1.1rem;
                padding: 12px;
                margin: 15px 0;
            }
            
            .date-info {
                font-size: 0.95rem;
            }
            
            .special-event {
                font-size: 1rem;
            }
        }
        
        /* 防止长按菜单 */
        .no-context-menu {
            -webkit-touch-callout: none;
            -webkit-user-select: none;
            -khtml-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }
    </style>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">
</head>
<body class="no-context-menu">
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
        <h2 id="surprise-title" style="margin: 10px 0; font-size: 1.3rem;">惊喜!</h2>
        <p id="surprise-content" style="margin: 15px 0; font-size: 1.1rem;">今天也是爱你的一天!</p>
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
        ];
        
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
        
        // 获取节气信息（简化版）
        function getSolarTerm(date) {
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
                {name: "七夕", month: 8, day: 25},
                {name: "中秋节", month: 9, day: 21},
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
        
        // 获取每日情话
        function getDailyLoveMessage(date) {
            const seed = date.year * 10000 + date.month * 100 + date.day;
            const index = seed % loveMessages.length;
            return loveMessages[index];
        }
        
        // 创建彩带效果（优化移动端性能）
        function createConfetti() {
            const colors = ['#e74c3c', '#3498db', '#2ecc71', '#f1c40f', '#9b59b6', '#1abc9c'];
            const confettiCount = isMobile() ? 50 : 100; // 移动端减少数量
            
            for (let i = 0; i < confettiCount; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = -10 + 'px';
                confetti.style.width = Math.random() * 8 + 4 + 'px';
                confetti.style.height = Math.random() * 8 + 4 + 'px';
                
                document.body.appendChild(confetti);
                
                const animationDuration = Math.random() * 2000 + 1500;
                
                const animation = confetti.animate([
                    { top: '-10px', opacity: 1, transform: 'rotate(0deg)' },
                    { top: '100vh', opacity: 0, transform: 'rotate(' + (Math.random() * 360) + 'deg)' }
                ], {
                    duration: animationDuration,
                    easing: 'cubic-bezier(0.1, 0.8, 0.3, 1)'
                });
                
                animation.onfinish = () => {
                    confetti.remove();
                };
            }
        }
        
        // 检测移动设备
        function isMobile() {
            return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent);
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
            
            // 点击外部关闭
            setTimeout(() => {
                document.addEventListener('click', closeSurpriseOnClickOutside, true);
            }, 100);
        }
        
        // 点击惊喜框外部关闭
        function closeSurpriseOnClickOutside(e) {
            const surpriseMsg = document.getElementById('surprise-message');
            if (!surpriseMsg.contains(e.target) && e.target.id !== 'heart-btn') {
                surpriseMsg.style.display = 'none';
                document.removeEventListener('click', closeSurpriseOnClickOutside, true);
            }
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
                if (!solarTerm) {
                    document.getElementById('special-message').textContent = festivalMessages[festival];
                    document.getElementById('special-message').style.display = 'block';
                }
            } else {
                document.getElementById('festival').textContent = '';
            }
            
            // 显示每日情话
            document.getElementById('daily-message').textContent = getDailyLoveMessage(date);
            
            // 爱心按钮事件（同时支持触摸和点击）
            const heartBtn = document.getElementById('heart-btn');
            heartBtn.addEventListener('click', handleHeartClick);
            heartBtn.addEventListener('touchend', handleHeartClick);
            
            // 关闭惊喜消息
            document.getElementById('close-surprise').addEventListener('click', function() {
                document.getElementById('surprise-message').style.display = 'none';
                document.removeEventListener('click', closeSurpriseOnClickOutside, true);
            });
            
            // 防止微信下拉露出背景
            document.addEventListener('touchmove', function(e) {
                if (e.target === document.documentElement || e.target === document.body) {
                    e.preventDefault();
                }
            }, { passive: false });
        }
        
        // 处理爱心点击（防抖）
        let lastClickTime = 0;
        function handleHeartClick(e) {
            e.preventDefault();
            const now = Date.now();
            if (now - lastClickTime < 1000) return; // 1秒内只响应一次
            
            lastClickTime = now;
            createConfetti();
            showSurpriseMessage();
            
            // 添加点击反馈
            const btn = e.currentTarget;
            btn.classList.remove('heartbeat');
            void btn.offsetWidth; // 触发重绘
            btn.classList.add('heartbeat');
        }
        
        // 页面加载完成后初始化
        document.addEventListener('DOMContentLoaded', initPage);
        
        // 微信浏览器特殊处理
        function isWeChat() {
            return /MicroMessenger/i.test(navigator.userAgent);
        }
        
        if (isWeChat()) {
            // 微信浏览器可能需要额外的样式调整
            document.body.style.height = window.innerHeight + 'px';
            window.addEventListener('resize', function() {
                document.body.style.height = window.innerHeight + 'px';
            });
        }
    </script>
</body>
</html>
