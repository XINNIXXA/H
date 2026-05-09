
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pour mon amour Habiba 💕</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Poppins:wght@300;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --pink-light: #fff0f3;
            --pink-soft: #ffb3c1;
            --pink-hot: #ff4d6d;
            --white: #ffffff;
            --text-color: #590d22;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--pink-light);
            font-family: 'Poppins', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            position: relative;
        }

        /* Arrière-plan animé */
        .floating-emojis {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .emoji {
            position: absolute;
            font-size: 1.5rem;
            animation: float 6s linear infinite;
            opacity: 0.6;
        }

        @keyframes float {
            0% { transform: translateY(110vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        /* La Carte Principale */
        .container {
            background: var(--white);
            padding: 3rem;
            border-radius: 30px;
            box-shadow: 0 15px 35px rgba(255, 77, 109, 0.1);
            text-align: center;
            z-index: 10;
            max-width: 500px;
            width: 90%;
            border: 2px solid var(--pink-soft);
            transition: all 0.5s ease;
        }

        .heart-icon {
            font-size: 4rem;
            color: var(--pink-hot);
            margin-bottom: 1rem;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            color: var(--text-color);
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        p {
            color: var(--text-mid);
            margin-bottom: 2rem;
            font-size: 1.1rem;
        }

        /* Boutons */
        .buttons {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            min-height: 150px;
        }

        button {
            border: none;
            cursor: pointer;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            font-family: 'Poppins', sans-serif;
        }

        #yesBtn {
            background-color: var(--pink-hot);
            color: white;
            padding: 15px 40px;
            font-size: 1.2rem;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.3);
        }

        #noBtn {
            background-color: var(--pink-soft);
            color: var(--text-color);
            padding: 12px 30px;
            font-size: 1rem;
        }

        /* Message de succès */
        #success-msg {
            display: none;
            animation: fadeIn 1s ease-in;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .dev-tag {
            position: absolute;
            bottom: 20px;
            font-size: 0.8rem;
            color: var(--pink-soft);
            letter-spacing: 2px;
            font-weight: 300;
        }

        .gif-container {
            width: 150px;
            margin: 0 auto 1rem;
        }
    </style>
</head>
<body>

    <div class="floating-emojis" id="emojiContainer"></div>

    <div class="container" id="mainCard">
        <div id="question-area">
            <div class="heart-icon">❤️</div>
            <h1>Ma chère Habiba...</h1>
            <p>Est-ce que tu m'aimes ? ✨</p>
            
            <div class="buttons">
                <button id="yesBtn" onclick="celebrate()">OUI ! ✨</button>
                <button id="noBtn" onclick="shrinkNo()">Non 🥺</button>
            </div>
        </div>

        <div id="success-msg">
            <div class="heart-icon">🥰</div>
            <h1>Je t'aime aussi Habiba !</h1>
            <p>Tu viens de me rendre la personne la plus heureuse au monde. ❤️✨</p>
            <div class="deco">🧸💍🎀</div>
        </div>
    </div>

    <div class="dev-tag">DEV BY XINN</div>

    <script>
        let noScale = 1;
        let yesScale = 1;
        const messages = [
            "Tu es sûre ?",
            "Réfléchis bien...",
            "Vraiment ?",
            "Habiba, s'il te plaît...",
            "Mon cœur va se briser 💔",
            "Dis oui !"
        ];
        let msgIndex = 0;

        // Fonction pour faire rétrécir le bouton NON
        function shrinkNo() {
            const noBtn = document.getElementById('noBtn');
            const yesBtn = document.getElementById('yesBtn');
            const p = document.querySelector('p');

            noScale -= 0.15;
            yesScale += 0.2;

            if (noScale <= 0.1) {
                noBtn.style.display = 'none';
            } else {
                noBtn.style.transform = `scale(${noScale})`;
                // Changer le texte du bouton Non pour être drôle
                noBtn.innerText = messages[msgIndex % messages.length];
                msgIndex++;
            }

            // Faire grandir le bouton OUI
            yesBtn.style.transform = `scale(${yesScale})`;
        }

        // Fonction de succès
        function celebrate() {
            document.getElementById('question-area').style.display = 'none';
            document.getElementById('success-msg').style.display = 'block';
            document.getElementById('mainCard').style.borderColor = '#ff4d6d';
            
            // Explosion de cœurs (optionnel mais sympa)
            for(let i=0; i<50; i++) {
                setTimeout(createEmoji, i * 50);
            }
        }

        // Création d'emojis flottants en arrière-plan
        const emojiList = ['🌸', '💕', '✨', '🧸', '💖', '💍'];
        const container = document.getElementById('emojiContainer');

        function createEmoji() {
            const emoji = document.createElement('div');
            emoji.className = 'emoji';
            emoji.innerText = emojiList[Math.floor(Math.random() * emojiList.length)];
            emoji.style.left = Math.random() * 100 + 'vw';
            emoji.style.animationDuration = (Math.random() * 3 + 4) + 's';
            container.appendChild(emoji);

            setTimeout(() => {
                emoji.remove();
            }, 6000);
        }

        setInterval(createEmoji, 500);
    </script>
</body>
</html>
