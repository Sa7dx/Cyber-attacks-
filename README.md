# Cyber-attacks-
You found the code ? Let’s see 
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>صفحة التح��ق</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        .card {
            background: white;
            padding: 2.5rem;
            border-radius: 15px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
            text-align: center;
            width: 100%;
            max-width: 350px;
            animation: slideIn 0.5s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        h3 {
            color: #333;
            margin-bottom: 1.5rem;
            font-size: 1.3rem;
        }

        input {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border: 2px solid #ddd;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        input:focus {
            outline: none;
            border-color: #667eea;
        }

        button {
            background-color: #28a745;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 8px;
            cursor: pointer;
            width: 100%;
            font-size: 1rem;
            font-weight: bold;
            transition: background-color 0.3s;
            margin-top: 10px;
        }

        button:hover {
            background-color: #218838;
        }

        button:active {
            transform: scale(0.98);
        }

        .hidden {
            display: none;
        }

        #message {
            color: red;
            font-size: 0.9rem;
            margin: 10px 0;
            min-height: 20px;
        }

        .success-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>

<div class="card">
    <!-- الخطوة الأولى: إدخال كلمة المرور -->
    <div id="step1">
        <h3>🔐 أدخل رمز الدخول</h3>
        <input type="password" id="passInput" placeholder="أدخل الرقم السري" autocomplete="off">
        <p id="message"></p>
        <button onclick="checkPassword()">تحقق</button>
    </div>

    <!-- الخطوة الثانية: استمارة جمع البيانات -->
    <div id="step2" class="hidden">
        <div class="success-icon">✨</div>
        <h3>أحسنت! ما هو اسمك؟</h3>
        <form action="https://formspree.io/f/YOUR_ID_HERE" method="POST">
            <input type="text" name="name" placeholder="اكتب اسمك هنا" required>
            <button type="submit">إرسال البيانات</button>
        </form>
    </div>
</div>

<script>
    function checkPassword() {
        const pass = document.getElementById('passInput').value;
        const msg = document.getElementById('message');
        
        if (pass === "699") {
            // إطلاق الاحتفالية (Confetti)
            confetti({
                particleCount: 150,
                spread: 70,
                origin: { y: 0.6 }
            });

            // الانتقال للخطوة التالية بعد ثانية واحدة
            setTimeout(() => {
                document.getElementById('step1').classList.add('hidden');
                document.getElementById('step2').classList.remove('hidden');
                document.getElementById('passInput').value = '';
            }, 1000);
            
        } else {
            msg.innerText = "❌ الرمز غير صحيح، حاول مجدداً!";
            document.getElementById('passInput').value = '';
            document.getElementById('passInput').focus();
        }
    }

    // السماح بالضغط على Enter لتقديم كلمة المرور
    document.getElementById('passInput').addEventListener('keypress', function(event) {
        if (event.key === 'Enter') {
            checkPassword();
        }
    });
</script>

</body>
</html>
