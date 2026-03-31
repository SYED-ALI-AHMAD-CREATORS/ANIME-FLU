# ANIME-FLU
ANIME FLU is a digital containment zone for the most potent stories, visuals, and soundtracks in the industry. Forget the mundane—we’re here to spread the obsession.Incubation Period:Be the first to witness new releases. Zero Resistance: A seamless, ad-light interface designed for pure binge-watching.
/* General Styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Poppins', sans-serif;
    background-color: #0b0c10;
    color: #ffffff;
    line-height: 1.6;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
}

/* Header */
.header {
    background: rgba(11, 12, 16, 0.95);
    padding: 1rem 0;
    position: fixed;
    width: 100%;
    top: 0;
    z-index: 1000;
    border-bottom: 1px solid #1f2833;
}

.header .container {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo h2 {
    color: #45f3ff;
    cursor: pointer;
}

.nav a {
    color: #fff;
    text-decoration: none;
    margin-right: 20px;
    transition: 0.3s;
}

.nav a:hover {
    color: #45f3ff;
}

.search-box {
    background: #1f2833;
    padding: 5px 15px;
    border-radius: 20px;
    display: flex;
    align-items: center;
}

.search-box input {
    background: transparent;
    border: none;
    color: white;
    outline: none;
    padding: 5px;
}

/* Hero Section */
.hero {
    height: 80vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(rgba(0,0,0,0.6), #0b0c10), url('https://via.placeholder.com/1920x1080/1a1a1a/45f3ff?text=Hero+Background');
    background-size: cover;
    margin-bottom: 40px;
    text-align: center;
}

.btn-primary {
    background: #45f3ff;
    color: #0b0c10;
    border: none;
    padding: 12px 30px;
    border-radius: 5px;
    font-weight: 600;
    cursor: pointer;
    margin-top: 20px;
    transition: 0.3s;
}

.btn-primary:hover {
    background: #fff;
    transform: scale(1.05);
}

/* Grid Layouts */
.section { padding: 40px 0; }
.section-title { margin-bottom: 25px; border-left: 4px solid #45f3ff; padding-left: 15px; }

.anime-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 20px;
}

/* Anime Card Component */
.anime-card {
    background: #1f2833;
    border-radius: 8px;
    overflow: hidden;
    transition: 0.3s;
    cursor: pointer;
}

.anime-card:hover {
    transform: translateY(-10px);
}

.anime-card img {
    width: 100%;
    height: 250px;
    object-fit: cover;
}

.anime-card-info {
    padding: 10px;
}

.anime-card-info h4 {
    font-size: 0.9rem;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

/* Footer */
.footer {
    text-align: center;
    padding: 40px 0;
    border-top: 1px solid #1f2833;
    margin-top: 50px;
    color: #666;
}
