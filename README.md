<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zajil Branch Service</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: #f4f6f9;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .card {
            background: #ffffff;
            width: 100%;
            max-width: 500px;
            padding: 2rem;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            border-top: 5px solid #0056b3;
        }

        h1 {
            color: #0056b3;
            font-size: 1.6rem;
            margin-bottom: 0.5rem;
            text-align: center;
        }

        p.subtitle {
            color: #666;
            text-align: center;
            font-size: 0.95rem;
            margin-bottom: 1.5rem;
        }

        .form-group {
            margin-bottom: 1.2rem;
        }

        label {
            display: block;
            margin-bottom: 0.4rem;
            font-weight: 600;
            font-size: 0.9rem;
        }

        input, select {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid #ccc;
            border-radius: 6px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input:focus, select:focus {
            border-color: #0056b3;
        }

        button {
            width: 100%;
            background-color: #0056b3;
            color: white;
            border: none;
            padding: 12px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            margin-top: 0.5rem;
            transition: background-color 0.2s;
        }

        button:hover {
            background-color: #004085;
        }

        .status-msg {
            margin-top: 1rem;
            padding: 10px;
            border-radius: 6px;
            display: none;
            text-align: center;
            font-size: 0.9rem;
        }

        .status-success {
            background-color: #d4edda;
            color: #155724;
        }
    </style>
</head>
<body>

    <div class="card">
        <h1>خدمات الفرع - Zajil</h1>
        <p class="subtitle">نظام الاستعلام عن خدمات وشحنات الفرع</p>

        <form id="serviceForm">
            <div class="form-group">
                <label for="trackingNo">رقم الشحنة / الطلب:</label>
                <input type="text" id="trackingNo" placeholder="أدخل الرقم هنا..." required>
            </div>

            <div class="form-group">
                <label for="serviceType">نوع الخدمة:</label>
                <select id="serviceType">
                    <option value="pickup">استلام من الفرع</option>
                    <option value="delivery">توصيل للعنوان</option>
                    <option value="inquiry">استفسار عام</option>
                </select>
            </div>

            <button type="submit">متابعة الطلب</button>
        </form>

        <div id="statusBox" class="status-msg status-success">
            تم استلام الطلب بنجاح، جاري المعالجة...
        </div>
    </div>

    <script>
        document.getElementById('serviceForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const trackingNo = document.getElementById('trackingNo').value;
            const statusBox = document.getElementById('statusBox');

            if(trackingNo.trim() !== '') {
                statusBox.style.display = 'block';
                statusBox.innerText = `تم استلام الطلب رقم (${trackingNo}) بنجاح!`;
            }
        });
    </script>
</body>
</html>
