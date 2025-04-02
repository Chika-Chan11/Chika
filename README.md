# Chika
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Suprise</title>
    <link rel="stylesheet" href="love.css">
    <link rel="stylesheet" href="main.css">
<div class="wallpaper"></div>
    <div class="content">
    </div>
</head>
<body>
    <div class="bg_heart">
        <div class="message"></div>
        <a href="love.html" class="next-button">Try tekan</a>
    </div>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="main.js"></script>
    <script src="love.js"></script>
<script>
    function setupMusic() {
        const music = document.getElementById('backgroundMusic');
        
        const isMusicPlaying = localStorage.getItem('musicPlaying') === 'true';
        const musicCurrentTime = localStorage.getItem('musicCurrentTime') || 0;

        if (isMusicPlaying) {
            music.currentTime = parseFloat(musicCurrentTime);
        }

        music.addEventListener('play', () => {
            localStorage.setItem('musicPlaying', 'true');
        });

        music.addEventListener('pause', () => {
            localStorage.setItem('musicPlaying', 'false');
        });

        setInterval(() => {
            localStorage.setItem('musicCurrentTime', music.currentTime);
        }, 1000);

        document.addEventListener('click', function startMusic() {
            music.play().catch(error => {
                console.log('Autoplay prevented', error);
            });
            document.removeEventListener('click', startMusic);
        });
    }

        document.addEventListener('DOMContentLoaded', setupMusic);
</script>

<audio id="backgroundMusic" loop>
    <source src="blue.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
</body>
</html>
