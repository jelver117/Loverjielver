<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>七夕专属 | 杰律的爱的告白</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #1a0229 0%, #2c0345 100%);
            color: #fff;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        /* 星星背景效果 */
        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        .star {
            position: absolute;
            background-color: #fff;
            border-radius: 50%;
            animation: twinkle 5s infinite;
        }
        
        @keyframes twinkle {
            0%, 100% { opacity: 0.2; }
            50% { opacity: 1; }
        }
        
        /* 爱心雨效果 */
        .hearts {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
        
        .heart {
            position: absolute;
            font-size: 20px;
            color: #ff2a70;
            opacity: 0.7;
            animation: fall 10s linear infinite;
        }
        
        @keyframes fall {
            0% {
                transform: translateY(-10%) rotate(0deg);
                opacity: 0.7;
            }
            100% {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }
        
        /* 登录容器 */
        .login-container {
            background: rgba(89, 10, 110, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            width: 100%;
            max-width: 450px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.5);
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .login-container::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 94, 157, 0.1), rgba(193, 34, 242, 0.1));
            transform: rotate(-45deg);
            z-index: 0;
        }
        
        .login-content {
            position: relative;
            z-index: 1;
        }
        
        .logo {
            font-size: 32px;
            font-weight: bold;
            margin-bottom: 30px;
            color: #ff5e9d;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .logo i {
            margin-right: 10px;
        }
        
        h1 {
            font-size: 28px;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #ff5e9d, #c122f2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            color: #d8b6e6;
            margin-bottom: 30px;
            font-size: 16px;
        }
        
        /* 输入框样式 */
        .input-group {
            margin-bottom: 25px;
            text-align: left;
        }
        
        .input-group label {
            display: block;
            margin-bottom: 8px;
            color: #e2c5f0;
            font-size: 14px;
        }
        
        .input-field {
            width: 100%;
            padding: 15px 20px;
            background: rgba(255, 255, 255, 0.08);
            border: 2px solid rgba(255, 255, 255, 0.1);
            border-radius: 12px;
            color: #fff;
            font-size: 16px;
            transition: all 0.3s;
        }
        
        .input-field:focus {
            outline: none;
            border-color: #c122f2;
            background: rgba(255, 255, 255, 0.12);
        }
        
        .input-field::placeholder {
            color: #b18bc9;
        }
        
        /* 按钮样式 */
        .login-btn {
            width: 100%;
            padding: 16px;
            background: linear-gradient(45deg, #ff5e9d, #c122f2);
            border: none;
            border-radius: 12px;
            color: white;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            margin-top: 10px;
        }
        
        .login-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 7px 15px rgba(193, 34, 242, 0.3);
        }
        
        .login-btn:active {
            transform: translateY(0);
        }
        
        /* 错误消息 */
        .error-message {
            color: #ff5e9d;
            margin-top: 15px;
            font-size: 14px;
            display: none;
        }
        
        /* 网站内容 - 默认隐藏 */
        .website-content {
            display: none;
            width: 100%;
        }
        
        /* 内容区域样式 */
        .content-section {
            background: rgba(89, 10, 110, 0.5);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
        }
        
        .content-section h2 {
            color: #ff5e9d;
            margin-bottom: 20px;
            font-size: 28px;
            text-align: center;
        }
        
        .message {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 20px;
            line-height: 1.6;
        }
        
        .photo-gallery {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 15px;
            margin-top: 20px;
        }
        
        .photo-placeholder {
            height: 180px;
            background: linear-gradient(45deg, #3a0457, #5c088f);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #d8b6e6;
            font-size: 14px;
            text-align: center;
            padding: 15px;
            transition: transform 0.3s;
        }
        
        .photo-placeholder:hover {
            transform: scale(1.05);
        }
        
        .countdown {
            font-size: 24px;
            text-align: center;
            margin: 20px 0;
            color: #ff5e9d;
            font-weight: bold;
        }
        
        .memory {
            display: flex;
            align-items: center;
            background: rgba(255, 255, 255, 0.08);
            border-radius: 15px;
            padding: 15px;
            margin-bottom: 15px;
        }
        
        .memory-date {
            min-width: 80px;
            text-align: center;
            color: #ff5e9d;
            font-weight: bold;
            margin-right: 15px;
        }
        
        .memory-content {
            flex: 1;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .login-container {
                padding: 30px 20px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .photo-gallery {
                grid-template-columns: 1fr 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- 星星背景 -->
    <div class="stars" id="stars"></div>
    
    <!-- 爱心雨 -->
    <div class="hearts" id="hearts"></div>
    
    <!-- 登录表单 -->
    <div class="login-container" id="loginContainer">
        <div class="login-content">
            <div class="logo">
                <i class="fas fa-heart"></i> 七夕之恋
            </div>
            <h1>爱的专属空间</h1>
            <p class="subtitle">请输入用户名和密码访问专属内容</p>
            
            <form id="loginForm">
                <div class="input-group">
                    <label for="username">用户名</label>
                    <input type="text" id="username" class="input-field" placeholder="请输入您的用户名" required>
                </div>
                
                <div class="input-group">
                    <label for="password">密码</label>
                    <input type="password" id="password" class="input-field" placeholder="请输入密码" required>
                </div>
                
                <button type="submit" class="login-btn">进入爱的世界</button>
                
                <div class="error-message" id="errorMessage">
                    <i class="fas fa-exclamation-circle"></i> 用户名或密码不正确
                </div>
            </form>
            
            <div style="margin-top: 20px; color: #b18bc9; font-size: 14px;">
                <p>提示: 用户名是"杰律"，密码是"iloveyou"</p>
            </div>
        </div>
    </div>
    
    <!-- 网站内容 -->
    <div class="website-content" id="websiteContent">
        <div class="content-section">
            <h2><i class="fas fa-heart"></i> 七夕快乐，我的爱人</h2>
            <div class="message">
                <p>亲爱的，在这个浪漫的七夕节，我想对你说：</p>
                <p>遇见你是我一生中最美好的意外，爱上你是我最幸福的决定。每一天和你在一起，都是我生命中最珍贵的时光。</p>
                <p>愿我们的爱情如同天上的牛郎织女，即使有银河相隔，也阻挡不了我们相爱的心。</p>
                <p>永远爱你的杰律</p>
            </div>
            
            <div class="countdown" id="countdown">
                我们已经相爱: 计算中...
            </div>
        </div>
        
        <div class="content-section">
            <h2><i class="fas fa-images"></i> 我们的甜蜜回忆</h2>
            <div class="photo-gallery">
                <div class="photo-placeholder">点击上传我们的第一张合影</div>
                <div class="photo-placeholder">点击上传第一次约会照片</div>
                <div class="photo-placeholder">点击上传旅行照片</div>
                <div class="photo-placeholder">点击上传日常生活照</div>
            </div>
        </div>
        
        <div class="content-section">
            <h2><i class="fas fa-history"></i> 我们的爱情历程</h2>
            
            <div class="memory">
                <div class="memory-date">2022-02-14</div>
                <div class="memory-content">我们第一次相遇，那天天空飘着细雨，你的笑容却像阳光一样照亮了我的世界</div>
            </div>
            
            <div class="memory">
                <div class="memory-date">2022-05-20</div>
                <div class="memory-content">你接受了我的告白，我们正式在一起了。这是我人生中最幸福的一天</div>
            </div>
            
            <div class="memory">
                <div class="memory-date">2023-01-22</div>
                <div class="memory-content">我们一起度过了第一个春节，虽然不能回家，但有你在身边就是家</div>
            </div>
            
            <div class="memory">
                <div class="memory-date">2023-06-01</div>
                <div class="memory-content">我们一起去了游乐园，你笑得像个孩子，那一刻我知道我找到了想要守护一生的人</div>
            </div>
        </div>
        
        <div class="content-section">
            <h2><i class="fas fa-gift"></i> 七夕礼物</h2>
            <div class="message">
                <p>今年七夕，我为你准备了特别的礼物：</p>
                <p>1. 你最喜欢的香水</p>
                <p>2. 手工制作的相册，记录我们的点点滴滴</p>
                <p>3. 一顿我亲手做的烛光晚餐</p>
                <p>4. 最重要的：我全部的爱和承诺</p>
            </div>
        </div>
    </div>

    <script>
        // 创建星星背景
        function createStars() {
            const stars = document.getElementById('stars');
            const starsCount = 200;
            
            for (let i = 0; i < starsCount; i++) {
                const star = document.createElement('div');
                star.classList.add('star');
                
                const size = Math.random() * 3;
                star.style.width = `${size}px`;
                star.style.height = `${size}px`;
                star.style.left = `${Math.random() * 100}%`;
                star.style.top = `${Math.random() * 100}%`;
                star.style.animationDelay = `${Math.random() * 5}s`;
                
                stars.appendChild(star);
            }
        }
        
        // 创建爱心雨
        function createHearts() {
            const hearts = document.getElementById('hearts');
            const heartsCount = 50;
            
            for (let i = 0; i < heartsCount; i++) {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '❤';
                
                heart.style.left = `${Math.random() * 100}%`;
                heart.style.animationDelay = `${Math.random() * 10}s`;
                heart.style.fontSize = `${Math.random() * 15 + 10}px`;
                
                hearts.appendChild(heart);
            }
        }
        
        // 处理登录表单提交
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorMessage = document.getElementById('errorMessage');
            
            // 验证用户名和密码
            if (username === '杰律' && password === 'iloveyou') {
                // 登录成功
                errorMessage.style.display = 'none';
                
                // 显示成功消息
                alert('登录成功！七夕快乐，我的爱人！❤');
                
                // 隐藏登录表单，显示网站内容
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('websiteContent').style.display = 'block';
                
                // 开始倒计时
                updateCountdown();
            } else {
                // 登录失败
                errorMessage.style.display = 'block';
                
                // 摇动效果
                const inputs = document.querySelectorAll('.input-field');
                inputs.forEach(input => {
                    input.classList.add('shake');
                    setTimeout(() => {
                        input.classList.remove('shake');
                    }, 500);
                });
            }
        });
        
        // 更新相爱时间倒计时
        function updateCountdown() {
            // 假设他们从2022年5月20日开始在一起
            const startDate = new Date('2022-05-20');
            const now = new Date();
            const diffTime = Math.abs(now - startDate);
            const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));
            const diffHours = Math.floor((diffTime % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            
            document.getElementById('countdown').textContent = 
                `我们已经相爱: ${diffDays} 天 ${diffHours} 小时`;
        }
        
        // 为照片占位符添加点击事件
        document.querySelectorAll('.photo-placeholder').forEach(photo => {
            photo.addEventListener('click', function() {
                alert('在实际应用中，这里可以实现照片上传功能。');
            });
        });
        
        // 初始化
        window.onload = function() {
            createStars();
            createHearts();
        };
    </script>
</body>
</html>