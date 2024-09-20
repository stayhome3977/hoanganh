<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="main.js"></script>
    <title>Trang web tính toán đơn giản</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h2 {
            text-align: center;
        }
        label, input {
            display: block;
            margin: 10px 0;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Phép Toán Cơ Bản</h2>

    <label for="num1">Nhập số a:</label>
    <input type="number" id="num1">

    <label for="num2">Nhập số b:</label>
    <input type="number" id="num2">

    <button onclick="tinhToan()">Thực hiện phép toán</button>
    <p id="result"></p>

    <h2>Giải Phương Trình Bậc Nhất</h2>
    <label for="a">Nhập hệ số a:</label>
    <input type="number" id="a">

    <label for="b">Nhập hằng số b:</label>
    <input type="number" id="b">

    <button onclick="giaiPhuongTrinh()">Giải phương trình</button>
    <p id="solution"></p>

    <h2>Tính Số Ngày Trong Tháng</h2>
    <label for="month">Nhập tháng (1-12):</label>
    <input type="number" id="month">

    <label for="year">Nhập năm:</label>
    <input type="number" id="year">

    <button onclick="tinhSoNgay()">Tính số ngày</button>
    <p id="days"></p>
</div>

<script>
    // Tính tổng, hiệu, tích, thương của hai số a và b
    function tinhToan() {
        var a = parseFloat(document.getElementById("num1").value);
        var b = parseFloat(document.getElementById("num2").value);
        if (!isNaN(a) && !isNaN(b)) {
            var tong = a + b;
            var hieu = a - b;
            var tich = a * b;
            var thuong = b !== 0 ? a / b : "Không thể chia cho 0";
            document.getElementById("result").innerHTML = "Tổng: " + tong + "<br>Hiệu: " + hieu + "<br>Tích: " + tich + "<br>Thương: " + thuong;
        } else {
            document.getElementById("result").innerHTML = "Vui lòng nhập số hợp lệ!";
        }
    }

    // Giải phương trình bậc nhất ax + b = 0
    function giaiPhuongTrinh() {
        var a = parseFloat(document.getElementById("a").value);
        var b = parseFloat(document.getElementById("b").value);
        if (!isNaN(a) && !isNaN(b)) {
            if (a !== 0) {
                var nghiem = -b / a;
                document.getElementById("solution").innerHTML = "Nghiệm của phương trình là: x = " + nghiem;
            } else {
                document.getElementById("solution").innerHTML = b === 0 ? "Phương trình vô số nghiệm" : "Phương trình vô nghiệm";
            }
        } else {
            document.getElementById("solution").innerHTML = "Vui lòng nhập số hợp lệ!";
        }
    }

    // Tính số ngày trong một tháng của năm
    function tinhSoNgay() {
        var month = parseInt(document.getElementById("month").value);
        var year = parseInt(document.getElementById("year").value);

        if (!isNaN(month) && !isNaN(year)) {
            var daysInMonth;
            if (month < 1 || month > 12) {
                daysInMonth = "Tháng không hợp lệ!";
            } else {
                if (month === 2) {
                    // Kiểm tra năm nhuận
                    daysInMonth = (year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0)) ? 29 : 28;
                } else if (month === 4 || month === 6 || month === 9 || month === 11) {
                    daysInMonth = 30;
                } else {
                    daysInMonth = 31;
                }
            }
            document.getElementById("days").innerHTML = "Số ngày trong tháng " + month + " năm " + year + " là: " + daysInMonth;
        } else {
            document.getElementById("days").innerHTML = "Vui lòng nhập tháng và năm hợp lệ!";
        }
    }
</script>

</body>
</html>
