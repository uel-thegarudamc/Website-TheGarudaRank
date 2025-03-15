# Website-TheGarudaRank
  <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jualan Rank TheGarudaMC</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Jualan rank TheGarudaMC</h1>
        <nav>
            <ul>
                <li><a href="#home">Beranda</a></li>
                <li><a href="#ranks">Rank</a></li>
                <li><a href="#contact">Kontak</a></li>
            </ul>
        </nav>
    </header>

    <section id="home">
        <h2>Selamat datang di sociabuzz TheGarudaMC</h2>
        <p>Dapatkan Rank yang kamu mau di sini!:]</p>
    </section>

    <section id="ranks">
        <h2>Daftar Rank</h2>
        <div class="rank-container">
            <div class="rank-card">
                <img src="img/rank1.png" alt="Rank 1">
                <h3>VIP-I</h3>
                <p>Rp 100.000</p>
                <button onclick="beliRank('VIP-I')">Beli</button>
            </div>
            
    <section id="ranks">
        <h3>Daftar Rank</h3>
        <div class="rank-container">
            <div class="rank-card">
                <img src="img/rank1.png" alt="Rank 2">
                <h3>VIP-II</h3>
                <p>Rp 100.000</p>
                <button onclick="beliRank('VIP-II')">Beli</button>
            </div>
                <section id="ranks">
        <h3>Daftar Rank</h3>
       <div class="rank-container">
            <div class="rank-card">
                <img src="img/rank2.png" alt="Rank 3">
                <h3>MVP-I</h3>
                <p>Rp 200.000</p>
                <button onclick="beliRank('MVP-I')">Beli</button>
            </div>
                <section id="ranks">
        <h3>Daftar Rank</h3>
       <div class="rank-container">
            <div class="rank-card">
                <img src="img/rank3.png" alt="Rank 4">
                <h3>Legend-I</h3>
                <p>Rp 300.000</p>
                <button onclick="beliRank('Legend-I')">Beli</button>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Hubungi Kami</h2>
        <p>WhatsApp: <a href="https://wa.me/6282331417860">Klik di sini</a></p>
    </section>

    <footer>
        <p>&copy;Dibuat oleh Sam:^]</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
<form id="checkout-form">
    <input type="hidden" id="rank-name" value="">
    <input type="hidden" id="rank-price" value="">
    <button type="submit">Bayar Sekarang</button>
</form>
<script src="script.js"></script>

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live2D Anime di Website</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background-color: #222;
            color: white;
            text-align: center;
        }
        #live2d-container {
            position: fixed;
            bottom: 0;
            right: 10px;
            width: 300px;
            height: 500px;
            pointer-events: none;
        }
    </style>
</head>
<body>

    <h1>Website Jualan Rank Minecraft</h1>
    <p>Selamat datang di website kami!</p>

    <canvas id="live2d" width="300" height="500"></canvas>

    <script src="https://unpkg.com/pixi.js/dist/pixi.min.js"></script>
    <script src="https://unpkg.com/live2d-widget/lib/L2Dwidget.min.js"></script>
    <script>
        L2Dwidget.init({
            model: {
                jsonPath: "https://unpkg.com/live2d-widget-model-shizuku/assets/shizuku.model.json",
            },
            display: {
                position: "right",
                width: 150,
                height: 300
            },
            mobile: {
                show: true,
                scale: 1
            },
            react: {
                opacityDefault: 1,
                opacityOnHover: 1
            }
        });
    </script>

</body>
</html>

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    text-align: center;
    background-color: #f0f0f0;
}

header {
    background: #2c3e50;
    color: white;
    padding: 15px;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 15px;
}

nav ul li a {
    color: white;
    text-decoration: none;
}

section {
    padding: 20px;
}

.rank-container {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
}

.rank-card {
    background: white;
    padding: 15px;
    border-radius: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
    text-align: center;
    width: 200px;
}

.rank-card img {
    width: 100%;
    height: auto;
}

button {
    background-color: #27ae60;
    color: white;
    border: none;
    padding: 10px;
    cursor: pointer;
}

button:hover {
    background-color: #219150;
}

footer {
    background: #2c3e50;
    color: white;
    padding: 10px;
}

function beliRank(rank) {
    alert("Anda telah memilih rank " + rank + ". Hubungi admin untuk melanjutkan pembayaran.");
}
document.querySelectorAll(".rank-card button").forEach(button => {
    button.addEventListener("click", function() {
        let rankName = this.parentElement.querySelector("h3").innerText;
        let rankPrice = this.parentElement.querySelector("p").innerText.replace("Rp ", "").replace(".", "");
        
        document.getElementById("rank-name").value = rankName;
        document.getElementById("rank-price").value = rankPrice;
        
        processPayment(rankName, rankPrice);
    });
});

function processPayment(rankName, rankPrice) {
    fetch("server.php", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ rank: rankName, price: rankPrice })
    })
    .then(response => response.json())
    .then(data => {
        window.location.href = data.redirect_url; // Redirect ke halaman pembayaran Midtrans
    })
    .catch(error => console.error("Error:", error));
}
$transaction_details = array(
    "transaction_details" => array(
        "order_id" => uniqid(),
        "gross_amount" => intval($request["price"])
    ),
    "customer_details" => array(
        "first_name" => "Pelanggan",
        "email" => "FAGSYP@gmail.com"
    )
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $api_url);
curl_setopt($ch, CURLOPT_HTTPHEADER, array(
    "Content-Type: application/json",
    "Authorization: Basic " . base64_encode($midtrans_server_key . ":")
));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($transaction_details));

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>

$transaction_details = array(
    "transaction_details" => array(
        "order_id" => uniqid(),
        "gross_amount" => intval($request["price"])
    ),
    "customer_details" => array(
        "first_name" => "Pelanggan",
        "email" => "FAGSYP@gmail.com"
    )
);

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $api_url);
curl_setopt($ch, CURLOPT_HTTPHEADER, array(
    "Content-Type: application/json",
    "Authorization: Basic " . base64_encode($midtrans_server_key . ":")
));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($transaction_details));

$response = curl_exec($ch);
curl_close($ch);

echo $response;
?>
