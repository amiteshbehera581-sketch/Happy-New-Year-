<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For You | 2026</title>
    <style>
        :root {
            --accent: #00d4ff; /* Electric Blue for 2026 vibes */
            --glow: rgba(0, 212, 255, 0.5);
            --bg: #0a0a0c;
        }

        body {
            margin: 0;
            background: var(--bg);
            color: white;
            font-family: 'Inter', -apple-system, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            text-align: center;
        }

        .container { z-index: 2; padding: 20px; }

        #countdown {
            font-size: 1.2rem;
            color: var(--accent);
            text-shadow: 0 0 10px var(--glow);
            margin-bottom: 20px;
            font-weight: bold;
        }

        h1 { font-size: 3.5rem; margin: 10px 0; letter-spacing: -1px; }

        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            padding: 40px;
            border-radius: 30px;
            display: none;
            max-width: 500px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        }

        .typewriter {
            font-size: 1.1rem;
            line-height: 1.6;
            color: #ccc;
            min-height: 100px;
        }

        button {
            background: white;
            color: black;
            border: none;
            padding: 18px 40px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            transition: 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        button:hover { transform: scale(1.1); box-shadow: 0 0 30px rgba(255,255,255,0.3); }

        /* Floating Stars */
        .star {
            position: absolute;
            background: white;
            border-radius: 50%;
            opacity: 0.5;
            animation: twinkle var(--duration) infinite;
        }

        @keyframes twinkle { 0%, 100% { opacity: 0.3; } 50% { opacity: 1; } }
    </style>
</head>
<body>

    <div class="container">
        <div id="countdown">Calculating 2026...</div>
        <h1 id="mainTitle">The Best is Yet to Come.</h1>
        
        <button id="revealBtn" onclick="startSurprise()">Open 2026 Message ✨</button>

        <div id="messageCard" class="glass-card">
            <div id="textTarget" class="typewriter"></div>
            <p style="margin-top: 30px; font-weight: bold; color: var(--accent);">Happy New Year 2026!</p>
        </div>
    </div>

    <script>
        // 1. Countdown to 2026
        function updateTimer() {
            const target = new Date('January 1, 2026 00:00:00').getTime();
            const now = new Date().getTime();
            const diff = target - now;

            if (diff < 0) {
                document.getElementById('countdown').innerHTML = "Welcome to 2026!";
                return;
            }

            const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const m = Math.floor((diff % (1000 * 60)) / (1000 * 60));
            const s = Math.floor((diff % (1000 * 60)) / 1000);
            
            document.getElementById('countdown').innerHTML = `2026 BEGINS IN: ${h}h ${m}m ${s}s`;
        }
        setInterval(updateTimer, 1000);

        // 2. Surprise Sequence
        const wishText = "As we step into 2026, my only wish is for you to see yourself the way I see you. You've been my anchor through 2025, and I can't wait to grow, laugh, and conquer another year by your side. You are my forever favorite. ✨";

        function startSurprise() {
            document.getElementById('revealBtn').style.display = 'none';
            document.getElementById('mainTitle').style.display = 'none';
            document.getElementById('messageCard').style.display = 'block';
            
            let i = 0;
            const target = document.getElementById('textTarget');
            function type() {
                if (i < wishText.length) {
                    target.innerHTML += wishText.charAt(i);
                    i++;
                    setTimeout(type, 50);
                }
            }
            type();
            createStars();
        }

        // 3. Background Effect
        function createStars() {
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                const size = Math.random() * 3 + 'px';
                star.style.width = size;
                star.style.height = size;
                star.style.left = Math.random() * 100 + 'vw';
                star.style.top = Math.random() * 100 + 'vh';
                star.style.setProperty('--duration', (Math.random() * 3 + 2) + 's');
                document.body.appendChild(star);
            }
        }
    </script>
</body>
</html>
