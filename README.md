
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AnimeStream - Ultra</title>
    <!-- Video.js & Themes -->
    <link href="https://vjs.zencdn.net/8.5.2/video-js.css" rel="stylesheet" />
    <link href="https://unpkg.com/@videojs/themes@1/dist/city/index.css" rel="stylesheet">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
<body class="dark-theme">

    <!-- Navigation -->
    <nav class="navbar">
        <div class="logo">ANIME<span>FLIX</span></div>
        <div class="search-bar">
            <input type="text" placeholder="Search anime...">
        </div>
        <div class="user-profile">
            <div class="premium-badge">VIP</div>
            <img src="https://i.pravatar.cc/40" alt="Avatar">
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="hero">
        <div class="hero-content">
            <span class="trending">#1 Trending</span>
            <h1>Attack on Titan</h1>
            <p>The final battle for humanity begins. Watch the epic conclusion now.</p>
            <div class="hero-btns">
                <button class="btn-play" onclick="openModal(1)">▶ Watch Now</button>
                <button class="btn-outline">+ Wishlist</button>
            </div>
        </div>
    </header>

    <!-- Video Player Modal -->
    <div id="videoModal" class="modal">
        <div class="modal-overlay" onclick="closeModal()"></div>
        <div class="modal-content container-fluid">
            <span class="close-modal" onclick="closeModal()">&times;</span>
            
            <div class="player-grid">
                <!-- Left: Video Area -->
                <div class="video-section">
                    <div class="player-container" id="playerWrapper">
                        <video id="animePlayer" class="video-js vjs-theme-city" controls preload="auto" width="100%">
                            <source src="https://vjs.zencdn.net/v/oceans.mp4" type="video/mp4">
                        </video>
                        <!-- Skip Intro Button -->
                        <button id="skipIntro" class="skip-btn hidden" onclick="skipIntro()">Skip Intro</button>
                    </div>

                    <div class="video-info">
                        <h2 id="currentTitle">Loading Episode...</h2>
                        <div class="player-options">
                            <button onclick="toggleTheater()"><i class="icon"></i> Theater Mode</button>
                            <button onclick="toggleLights()"><i class="icon"></i> Lights Out</button>
                            <label><input type="checkbox" id="autoNext" checked> Auto-Next</label>
                        </div>
                    </div>
                </div>

                <!-- Right: Playlist -->
                <div class="playlist-section">
                    <h3>Episodes</h3>
                    <div id="playlist" class="custom-scrollbar">
                        <!-- Episodes injected by JS -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://vjs.zencdn.net/8.5.2/video.min.js"></script>
    <script src="script.js"></script>
</body>
</html>:root {
    --primary: #e50914;
    --bg-dark: #0a0a0a;
    --card-bg: rgba(255, 255, 255, 0.1);
    --glass: rgba(20, 20, 20, 0.85);
}

body {
    margin: 0;
    font-family: 'Inter', sans-serif;
    background-color: var(--bg-dark);
    color: white;
    overflow-x: hidden;
}

/* Glassmorphism Navbar */
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 15px 5%;
    position: fixed;
    width: 100%;
    z-index: 100;
    background: linear-gradient(to bottom, rgba(0,0,0,0.8) 0%, transparent 100%);
    backdrop-filter: blur(10px);
}

.logo { font-weight: 800; font-size: 1.5rem; color: white; cursor: pointer; }
.logo span { color: var(--primary); }

/* Hero Section */
.hero {
    height: 80vh;
    background: linear-gradient(to right, rgba(0,0,0,0.9), transparent), 
                url('https://images.alphacoders.com/132/1329188.jpeg');
    background-size: cover;
    display: flex;
    align-items: center;
    padding: 0 5%;
}

.hero-content h1 { font-size: 4rem; margin: 10px 0; }
.btn-play { 
    background: var(--primary); color: white; border: none; 
    padding: 12px 30px; font-weight: bold; border-radius: 4px; cursor: pointer;
    transition: 0.3s;
}
.btn-play:hover { transform: scale(1.05); background: #ff0f1b; }

/* Modal & Player Grid */
.modal {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 1000;
}

.modal-overlay {
    position: absolute;
    inset: 0;
    background: rgba(0,0,0,0.95);
    backdrop-filter: blur(5px);
}

.modal-content {
    position: relative;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 95vw;
    max-width: 1300px;
    background: #141414;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 0 50px rgba(0,0,0,1);
}

.player-grid {
    display: grid;
    grid-template-columns: 1fr 350px;
}

.video-section { padding: 20px; }
.playlist-section {
    background: #1a1a1a;
    padding: 20px;
    border-left: 1px solid #333;
}

/* Video.js Customization */
.video-js {
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
}

/* Skip Intro Button */
.skip-btn {
    position: absolute;
    bottom: 80px;
    right: 20px;
    background: rgba(0,0,0,0.8);
    color: white;
    border: 1px solid white;
    padding: 10px 20px;
    cursor: pointer;
    z-index: 10;
}

.hidden { display: none; }

/* Episode Cards */
.ep-card {
    display: flex;
    gap: 10px;
    padding: 10px;
    margin-bottom: 10px;
    background: #252525;
    border-radius: 5px;
    cursor: pointer;
    transition: 0.2s;
}
.ep-card:hover { background: #333; }
.ep-card.active { border-left: 4px solid var(--primary); background: #2a2a2a; }
.ep-thumb { width: 100px; height: 60px; object-fit: cover; border-radius: 4px; }

/* Theater Mode Class */
.theater-mode .player-grid { grid-template-columns: 1fr; }
.theater-mode .playlist-section { display: none; }
.theater-mode .modal-content { max-width: 100vw; width: 100vw; height: 100vh; top:0; left:0; transform:none; }

/* Custom Scrollbar */
.custom-scrollbar::-webkit-scrollbar { width: 6px; }
.custom-scrollbar::-webkit-scrollbar-thumb { background: #444; border-radius: 10px; }const episodes = [
    { id: 1, title: "To You, 2000 Years Later", thumb: "https://via.placeholder.com/100x60", url: "https://vjs.zencdn.net/v/oceans.mp4", introStart: 5, introEnd: 15 },
    { id: 2, title: "That Day", thumb: "https://via.placeholder.com/100x60", url: "https://media.w3.org/2010/05/sintel/trailer.mp4", introStart: 2, introEnd: 10 },
    { id: 3, title: "A Dim Light Amid Despair", thumb: "https://via.placeholder.com/100x60", url: "https://media.w3.org/2010/05/bunny/movie.mp4", introStart: 0, introEnd: 0 }
];

let currentEpIndex = 0;
const player = videojs('animePlayer');

// 1. Open Modal & Load Data
function openModal(id) {
    document.getElementById("videoModal").style.display = "block";
    renderPlaylist();
    loadEpisode(0);
}

function closeModal() {
    document.getElementById("videoModal").style.display = "none";
    player.pause();
}

// 2. Load Episode Logic
function loadEpisode(index) {
    currentEpIndex = index;
    const ep = episodes[index];
    
    player.src({ type: 'video/mp4', src: ep.url });
    document.getElementById("currentTitle").innerText = `Ep ${ep.id} - ${ep.title}`;
    
    // Update Active UI
    renderPlaylist();
    player.play();
}

// 3. Skip Intro Logic
player.on('timeupdate', function() {
    const ep = episodes[currentEpIndex];
    const currentTime = player.currentTime();
    const skipBtn = document.getElementById("skipIntro");

    if (currentTime >= ep.introStart && currentTime <= ep.introEnd) {
        skipBtn.classList.remove("hidden");
    } else {
        skipBtn.classList.add("hidden");
    }
});

function skipIntro() {
    const ep = episodes[currentEpIndex];
    player.currentTime(ep.introEnd);
}

// 4. Auto-Next Logic
player.on('ended', function() {
    if (document.getElementById("autoNext").checked) {
        if (currentEpIndex < episodes.length - 1) {
            loadEpisode(currentEpIndex + 1);
        }
    }
});

// 5. Theater Mode & Effects
function toggleTheater() {
    document.body.classList.toggle("theater-mode");
    player.fluid(true); 
}

function toggleLights() {
    const overlay = document.querySelector(".modal-overlay");
    overlay.style.background = overlay.style.background === "black" ? "rgba(0,0,0,0.9)" : "black";
}

// 6. Keyboard Shortcuts
document.addEventListener('keydown', (e) => {
    if (document.getElementById("videoModal").style.display === "block") {
        if (e.code === "Space") { e.preventDefault(); player.paused() ? player.play() : player.pause(); }
        if (e.code === "KeyF") { player.requestFullscreen(); }
        if (e.code === "KeyM") { player.muted(!player.muted()); }
    }
});

// 7. Render Playlist UI
function renderPlaylist() {
    const container = document.getElementById("playlist");
    container.innerHTML = episodes.map((ep, index) => `
        <div class="ep-card ${index === currentEpIndex ? 'active' : ''}" onclick="loadEpisode(${index})">
            <img src="${ep.thumb}" class="ep-thumb">
            <div>
                <div style="font-size: 0.8rem; color: #888;">Episode ${ep.id}</div>
                <div style="font-size: 0.9rem; font-weight: 600;">${ep.title}</div>
            </div>
        </div>
    `).join('');
}
