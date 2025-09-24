<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>黄秋婧的生日贺卡</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Microsoft YaHei', sans-serif;
            overflow: hidden;
            background: linear-gradient(135deg, #ffd166 0%, #ff9a8b 50%, #ff6b6b 100%);
            position: relative;
            height: 100vh;
        }

        /* 背景动画元素 */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .falling-item {
            position: absolute;
            animation: fall linear infinite;
        }

        @keyframes fall {
            to {
                transform: translateY(100vh) rotate(360deg);
            }
        }

        .leaf {
            width: 30px;
            height: 30px;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><path d="M50 10 Q30 30 20 50 Q10 70 20 85 Q30 95 50 90 Q70 95 80 85 Q90 70 80 50 Q70 30 50 10" fill="%23ff6b6b"/></svg>') no-repeat center;
            background-size: contain;
        }

        .star {
            width: 20px;
            height: 20px;
            background: radial-gradient(circle, #fff 0%, transparent 70%);
            border-radius: 50%;
            animation: twinkle 2s infinite, fall linear infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 1; }
        }

        .confetti {
            width: 10px;
            height: 10px;
            background: #ffd166;
            animation: confetti-fall 3s infinite;
        }

        @keyframes confetti-fall {
            0% { transform: translateY(-100vh) rotate(0deg); }
            100% { transform: translateY(100vh) rotate(720deg); }
        }

        /* 主容器 */
        .card-container {
            position: relative;
            width: 100%;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 10;
        }

        .page {
            position: absolute;
            width: 80%;
            max-width: 800px;
            height: 80%;
            background: rgba(255, 255, 255, 0.85);
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.1);
            display: none;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 40px;
            animation: pageIn 0.6s ease-out;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        @keyframes pageIn {
            from {
                opacity: 0;
                transform: translateX(100px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .page.active {
            display: flex;
        }

        /* 首页特殊样式 */
        .home-page .date-box {
            background: rgba(255, 255, 255, 0.9);
            padding: 20px 40px;
            border-radius: 15px;
            margin: 10px;
            font-size: 24px;
            color: #ff6b6b;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
            opacity: 0;
            animation: fadeIn 1s forwards;
            border: 1px solid rgba(255, 255, 255, 0.5);
        }

        .home-page .date-box.second {
            animation-delay: 0.5s;
        }

        @keyframes fadeIn {
            to {
                opacity: 1;
                transform: translateY(-10px);
            }
        }

        .home-text {
            margin-top: 30px;
            font-size: 20px;
            color: #ff6b6b;
            opacity: 0;
            animation: fadeIn 1s 1s forwards;
            font-weight: bold;
        }

        .start-arrow {
            margin-top: 30px;
            font-size: 40px;
            color: #ff6b6b;
            cursor: pointer;
            opacity: 0;
            animation: fadeIn 1s 1.5s forwards, bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        /* 普通页面样式 */
        .page-image {
            max-width: 60%;
            max-height: 50%;
            object-fit: contain;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            margin-bottom: 30px;
        }

        .page-text {
            font-size: 24px;
            color: #ff6b6b;
            text-align: center;
            line-height: 1.6;
            margin-bottom: 30px;
            font-weight: bold;
            text-s
