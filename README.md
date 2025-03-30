# Zakaz-Booss
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Zakaz Boss</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://sdmntpreastus2.oaiusercontent.com/files/00000000-b980-51f6-be7a-4bb88e99955f/raw?se=2025-03-29T14%3A20%3A25Z&sp=r&sv=2024-08-04&sr=b&scid=1623f740-d9c7-5fc2-8836-92b110289b52&skoid=ac1d63ad-0c69-4017-8785-7a50eb04382c&sktid=a48cca56-e6da-484e-a814-9c849652bcb3&skt=2025-03-29T07%3A53%3A34Z&ske=2025-03-30T07%3A53%3A34Z&sks=b&skv=2024-08-04&sig=Zaf4Ufl7XhAe0Isj8yW0lLHCs4RvsOwXdN%2BLU4F8xI4%3D') no-repeat center center fixed;
            background-size: cover;
            color: white;
            text-align: center;
            user-select: none;
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
        }
        .container {
            max-width: 500px;
            margin: 50px auto;
            background: rgba(255, 255, 255, 0.1);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
        }
        input, button {
            padding: 10px;
            margin: 5px;
            border: none;
            border-radius: 5px;
        }
        input {
            width: 70%;
        }
        button {
            cursor: pointer;
            background: #ff7eb3;
            color: white;
        }
        .order {
            background: white;
            color: black;
            margin: 10px;
            padding: 10px;
            border-radius: 5px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
    </style>
    <script>
        document.addEventListener('keydown', function (event) {
            if (event.key === "PrintScreen") {
                event.preventDefault();
                alert('Skrinshot olish taqiqlangan!');
            }
        });
        document.addEventListener('keyup', function (event) {
            if (event.key === "PrintScreen") {
                navigator.clipboard.writeText("");
            }
        });
        
        document.addEventListener("DOMContentLoaded", function() {
            const style = document.createElement("style");
            style.innerHTML = `
                html, body {
                    -webkit-touch-callout: none;
                    -webkit-user-select: none;
                    -khtml-user-select: none;
                    -moz-user-select: none;
                    -ms-user-select: none;
                    user-select: none;
                }
                @media screen and (-webkit-min-device-pixel-ratio:0) {
                    * {
                        -webkit-user-select: none;
                        -webkit-touch-callout: none;
                    }
                }
            `;
            document.head.appendChild(style);
        });
    </script>
</head>
<body>
    <div class="container">
        <h2>Zakaz Qo'shish</h2>
        <input type="text" id="orderName" placeholder="Zakaz nomi">
        <input type="number" id="orderPrice" placeholder="Narx (so'm)">
        <input type="text" id="orderDeliverer" placeholder="Kim olib keladi">
        <input type="text" id="orderImage" placeholder="Rasm URL">
        <button onclick="addOrder()">Qo'shish</button>
        <h2>Zakazlar Ro'yxati</h2>
        <div id="orderList"></div>
        <h3>To'lov bo‘yicha bog‘lanish: <a href="https://t.me/ahror_0511" target="_blank">@ahror_0511</a></h3>
    </div>

    <script>
        const ownerCardNumber = "8600123456789012";
        
        const predefinedOrders = [
            { name: "1-mashina", price: "100000", deliverer: "Maxsus Xizmat", image: "https://example.com/image1.jpg" }
        ];

        function loadPredefinedOrders() {
            let orderList = document.getElementById('orderList');
            predefinedOrders.forEach(order => {
                let div = document.createElement('div');
                div.className = 'order';
                div.innerHTML = `<p>${order.name}</p>
                    <p>Narx: ${order.price} so'm</p>
                    <p>Olib keluvchi: ${order.deliverer}</p>
                    <img src="${order.image}" alt="Order Image"> 
                    <button onclick="payWithPayme('${order.price}')">Payme orqali to'lash</button>
                    <button onclick="payWithClick('${order.price}')">Click orqali to'lash</button>
                    <button onclick="deleteOrder(this)">O'chirish</button>`;
                orderList.appendChild(div);
            });
        }

        function addOrder() {
            let orderName = document.getElementById('orderName').value;
            let orderPrice = document.getElementById('orderPrice').value;
            let orderDeliverer = document.getElementById('orderDeliverer').value;
            let orderImage = document.getElementById('orderImage').value;
            
            if (orderName === '' || orderPrice === '' || orderDeliverer === '' || orderImage === '') {
                alert('Barcha maydonlarni to‘ldiring!');
                return;
            }
            
            let orderList = document.getElementById('orderList');
            let div = document.createElement('div');
            div.className = 'order';
            div.innerHTML = `<p>${orderName}</p>
                <p>Narx: ${orderPrice} so'm</p>
                <p>Olib keluvchi: ${orderDeliverer}</p>
                <img src="${orderImage}" alt="Order Image"> 
                <button onclick="payWithPayme('${orderPrice}')">Payme orqali to'lash</button>
                <button onclick="payWithClick('${orderPrice}')">Click orqali to'lash</button>
                <button onclick="deleteOrder(this)">O'chirish</button>`;
            orderList.appendChild(div);
        }
    </script>
</body>
</html>
