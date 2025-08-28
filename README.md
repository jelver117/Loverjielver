# Loverjielver
For my lover
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我们的七夕节 | 爱的纪念</title>
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
        
        /* 额外选项 */
        .extra-options {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 20px;
            font-size: 14px;
            color: #b18bc9;
        }
        
        .remember-me {
            display: flex;
            align-items: center;
        }
        
        .remember-me input {
            margin-right: 8px;
        }
        
        .forgot-password {
            color: #ff5e9d;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .forgot-password:hover {
            color: #fff;
        }
        
        /* 错误消息 */
        .error-message {
            color: #ff5e9d;
            margin-top: 15px;
            font-size: 14px;
            display: none;
        }
        
        /* 响应式设计 */
        @media (max-width: 500px) {
            .login-container {
                padding: 30px 20px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .extra-options {
                flex-direction: column;
                gap: 10px;
                align-items: flex-start;
            }
        }
        
        /* 网站内容 - 默认隐藏 */
        .website-content {
            display: none;
            width: 100%;
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
            <h1>专属访问</h1>
            <p class="subtitle">请输入密码查看专属内容</p>
            
            <form id="loginForm">
                <div class="input-group">
                    <label for="username">你的名字</label>
                    <input type="text" id="username" class="input-field" placeholder="请输入你的名字" required>
                </div>
                
                <div class="input-group">
                    <label for="password">访问密码</label>
                    <input type="password" id="password" class="input-field" placeholder="请输入密码" required>
                </div>
                
                <button type="submit" class="login-btn">进入我们的世界</button>
                
                <div class="error-message" id="errorMessage">
                    <i class="fas fa-exclamation-circle"></i> 密码不正确，请再试一次
                </div>
            </form>
            
            <div class="extra-options">
                <div class="remember-me">
                    <input type="checkbox" id="rememberMe">
                    <label for="rememberMe">记住我</label>
                </div>
                <a href="#" class="forgot-password">忘记密码？</a>
            </div>
        </div>
    </div>
    
    <!-- 网站内容 -->
    <div class="website-content" id="websiteContent">
        <!-- 这里放置您之前创建的网站内容 -->
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
            
            // 简单验证 - 在实际应用中，这应该与后端验证
            if (password === 'iloveyou' || password === '5201314' || password === 'qixi2023') {
                // 登录成功
                errorMessage.style.display = 'none';
                
                // 显示成功消息
                alert('登录成功！欢迎进入我们的世界，' + username + '！❤');
                
                // 隐藏登录表单，显示网站内容
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('websiteContent').style.display = 'block';
                
                // 在实际应用中，这里可以重定向到主页面或显示隐藏的内容
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
        
        // 忘记密码链接
        document.querySelector('.forgot-password').addEventListener('click', function(e) {
            e.preventDefault();
            alert('提示：试试这些密码之一：iloveyou, 5201314, qixi2023\n\n当然，在实际应用中，这会通过邮件重置。');
        });
        
        // 初始化
        window.onload = function() {
            createStars();
            createHearts();
            
            // 检查是否已登录（本地存储示例）
            if (localStorage.getItem('isLoggedIn') === 'true') {
                document.getElementById('loginContainer').style.display = 'none';
                document.getElementById('websiteContent').style.display = 'block';
            }
        };
    </script>
</body>
</html>