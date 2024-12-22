# Major-Match
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="icon" type="image/png" href="website/MajorMatch.png">
    <title>MajorMatch</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            flex-direction: column;
            background-image: url('https://cdn.pixabay.com/photo/2021/01/21/15/54/books-5937716_1280.jpg');
            background-size: cover;
            background-repeat: no-repeat;
            background-position: center;
        }
        .welcome-container {
            text-align: center;
        }
        .welcome-container h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: white;
            padding: 5px 10px;
            border-radius: 5px;
        }
        .welcome-container p {
            font-size: 1.2rem;
            margin-bottom: 25rem;
            color: white;
        }
        .welcome-container button {
            padding: 10px 20px;
            font-size: 1.2rem;
            background-color: #ff9900;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            position: absolute;
            bottom: 380px; /* Tombol diposisikan 20px dari bawah */
            right: 675px; /* Tombol diposisikan 20px dari kanan */
        }
        .welcome-container button:hover {
            background-color: #872b00;
        }
    </style>
</head>
<body>
    <div class="welcome-container">
        <h1>Welcome to MajorMatch!</h1>
        <p>Find your best major with your favourite lesson!</p>
        <button onclick="startWebsite()">Mulai</button>
    </div>

    <script>
        function startWebsite() {
            // Redirect ke halaman utama
            window.location.href = "major-match.html"; // Ganti dengan nama file HTML utama Anda
        }
    </script>
</body>
</html>
