<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>우리카페 WorldBanksPi 스테이킹 갯수는?</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            flex-direction: column;
            text-align: center;
        }
        h1 {
            color: #333;
            font-size: 1.5em;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            max-width: 400px;
            width: 100%;
        }
        input[type="number"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        button {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 1em;
        }
        button:hover {
            background-color: #45a049;
        }
        #total {
            font-size: 1.2em;
            margin-top: 20px;
            color: #007BFF;
        }
        @media (max-width: 600px) {
            h1 {
                font-size: 1.2em;
            }
            .container {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>우리 카페에서 스테이킹한 WorldBanksPi 갯수?</h1>
        <p>익명성이 보장됩니다. 누적 총계가 업데이트됩니다.</p>
        <input type="number" id="stakingAmount" placeholder="스테이킹 갯수 입력 (숫자만)" min="0" step="1" required>
        <button onclick="addStaking()">입력하기</button>
        <div id="total">현재 누적 스테이킹: 0 개</div>
    </div>

    <script>
        // 로컬 스토리지에서 누적 값 불러오기
        let totalStaking = localStorage.getItem('totalStaking') ? parseInt(localStorage.getItem('totalStaking')) : 0;
        document.getElementById('total').innerText = `현재 누적 스테이킹: ${totalStaking} 개`;

        function addStaking() {
            const amountInput = document.getElementById('stakingAmount');
            const amount = parseInt(amountInput.value);
            
            if (isNaN(amount) || amount < 0) {
                alert('유효한 숫자를 입력하세요 (0 이상).');
                return;
            }
            
            totalStaking += amount;
            localStorage.setItem('totalStaking', totalStaking);
            document.getElementById('total').innerText = `현재 누적 스테이킹: ${totalStaking} 개`;
            amountInput.value = ''; // 입력 필드 초기화
        }
    </script>
</body>
</html>
