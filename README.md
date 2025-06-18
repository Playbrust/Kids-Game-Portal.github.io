<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kids Game Portal</title>
    <link href="https://fonts.googleapis.com/css2?family=Comic+Neue:wght@400;700&family=Fredoka+One&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #FF6B6B;
            --secondary: #4ECDC4;
            --accent: #FFE66D;
            --background: #F7FFF7;
            --text: #292F36;
            --card-bg: #FFFFFF;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Comic Neue', cursive;
            background-color: var(--background);
            color: var(--text);
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
            animation: bounce 2s infinite;
        }

        h1 {
            font-family: 'Fredoka One', cursive;
            color: var(--primary);
            font-size: 3rem;
            margin-bottom: 10px;
            text-shadow: 3px 3px 0 rgba(0,0,0,0.1);
        }

        .subtitle {
            color: var(--secondary);
            font-size: 1.2rem;
        }

        .search-container {
            max-width: 600px;
            margin: 0 auto 30px;
            position: relative;
        }

        #search {
            width: 100%;
            padding: 15px 20px;
            border-radius: 50px;
            border: 3px solid var(--accent);
            font-size: 1.1rem;
            font-family: 'Comic Neue', cursive;
            outline: none;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: all 0.3s;
        }

        #search:focus {
            border-color: var(--secondary);
            box-shadow: 0 4px 12px rgba(78, 205, 196, 0.2);
        }

        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 25px;
            padding: 10px;
        }

        .game-card {
            background-color: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 6px 12px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
            border: 3px solid transparent;
        }

        .game-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0,0,0,0.15);
            border-color: var(--accent);
        }

        .game-icon {
            width: 100%;
            height: 150px;
            object-fit: contain;
            padding: 15px;
            background-color: white;
        }

        .game-name {
            padding: 15px;
            font-weight: bold;
            color: var(--text);
            background-color: var(--accent);
            font-size: 1.1rem;
        }

        .no-results {
            text-align: center;
            grid-column: 1 / -1;
            padding: 40px;
            color: var(--primary);
            font-size: 1.5rem;
        }

        .loading {
            text-align: center;
            padding: 40px;
            font-size: 1.5rem;
            color: var(--secondary);
        }

        .spinner {
            border: 5px solid rgba(78, 205, 196, 0.2);
            border-radius: 50%;
            border-top: 5px solid var(--secondary);
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }

        .disclaimer {
            max-width: 800px;
            margin: 40px auto;
            padding: 20px;
            background-color: var(--card-bg);
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            font-size: 0.9rem;
            line-height: 1.6;
            border-left: 5px solid var(--primary);
        }

        .disclaimer h2 {
            color: var(--primary);
            margin-bottom: 15px;
            font-family: 'Fredoka One', cursive;
        }

        .disclaimer p {
            margin-bottom: 10px;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        @media (max-width: 768px) {
            .games-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            }
            
            h1 {
                font-size: 2.2rem;
            }
        }

        @media (max-width: 480px) {
            .games-grid {
                grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
                gap: 15px;
            }
            
            .game-icon {
                height: 120px;
            }
            
            .game-name {
                font-size: 0.9rem;
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Kids Game Portal</h1>
        <p class="subtitle">Click any game to start playing!</p>
    </header>

    <div class="search-container">
        <input type="text" id="search" placeholder="Search for games...">
    </div>

    <div id="games-container">
        <div class="loading">
            <div class="spinner"></div>
            <p>Loading games...</p>
        </div>
    </div>

    <div class="disclaimer">
        <h2>Educational Purpose Disclaimer</h2>
        <p>This Kids Game Portal is created solely for educational purposes to demonstrate web development concepts including HTML, CSS, and JavaScript. The portal is not intended for commercial use or actual distribution to children.</p>
        
        <p><strong>Important Information for Parents and Educators:</strong></p>
        <p>1. This website is part of an educational demonstration and should not be considered a fully vetted or secured platform for children.</p>
        <p>2. Any games linked from this portal are external resources not controlled by the creator of this educational project.</p>
        <p>3. Parents and educators should always review and approve any online content before allowing children to access it.</p>
        <p>4. No personal data is collected by this website, but external sites may have their own privacy policies.</p>
        <p>5. The creator of this educational project makes no representations or warranties of any kind about the safety, appropriateness, or educational value of any linked games.</p>
        
        <p><strong>For Students and Developers:</strong></p>
        <p>This project demonstrates several web development techniques including:</p>
        <ul>
            <li>Responsive design with CSS Grid and Flexbox</li>
            <li>Dynamic content loading from external data sources</li>
            <li>Search functionality implementation</li>
            <li>Error handling and user feedback</li>
            <li>Accessibility considerations in design</li>
        </ul>
        <p>The code is provided as a learning resource and should be adapted with proper attribution for any educational or personal use.</p>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Your Google Sheets CSV export URL
            const csvUrl = 'https://docs.google.com/spreadsheets/d/1Rab3ElYa-_jIw8X5FoQB69MKdCmD9nf9jVKxnc058G0/export?format=csv';
            
            // First try to fetch directly
            fetch(csvUrl)
                .then(response => {
                    if (!response.ok) {
                        throw new Error('Direct fetch failed');
                    }
                    return response.text();
                })
                .then(csvData => {
                    const games = parseCSV(csvData);
                    displayGames(games);
                    setupSearch(games);
                })
                .catch(error => {
                    console.log('Direct fetch failed, trying proxy method');
                    // If direct fetch fails, try using a CORS proxy
                    return fetch(`https://api.allorigins.win/get?url=${encodeURIComponent(csvUrl)}`)
                        .then(response => response.json())
                        .then(data => {
                            const games = parseCSV(data.contents);
                            displayGames(games);
                            setupSearch(games);
                        })
                        .catch(proxyError => {
                            console.error('Both methods failed:', proxyError);
                            showError();
                        });
                });

            function parseCSV(csv) {
                const lines = csv.split('\n');
                const games = [];
                
                for (let i = 0; i < lines.length; i++) {
                    const line = lines[i].trim();
                    if (line) {
                        // Split by tab or comma
                        const parts = line.includes('\t') ? line.split('\t') : line.split(',');
                        if (parts.length >= 3) {
                            games.push({
                                name: parts[0].trim(),
                                icon: parts[1].trim(),
                                link: parts[2].trim()
                            });
                        }
                    }
                }
                
                return games;
            }

            function displayGames(games) {
                const container = document.getElementById('games-container');
                
                if (games.length === 0) {
                    container.innerHTML = '<div class="no-results">No games found</div>';
                    return;
                }
                
                let html = '<div class="games-grid">';
                
                games.forEach(game => {
                    html += `
                        <div class="game-card" data-name="${game.name.toLowerCase()}">
                            <img src="${game.icon || 'https://via.placeholder.com/150?text=Game'}" 
                                 alt="${game.name}" 
                                 class="game-icon"
                                 onerror="this.src='https://via.placeholder.com/150?text=Game'">
                            <div class="game-name">${game.name}</div>
                        </div>
                    `;
                });
                
                html += '</div>';
                container.innerHTML = html;
                
                // Add click event to all game cards
                document.querySelectorAll('.game-card').forEach(card => {
                    const gameName = card.getAttribute('data-name');
                    const game = games.find(g => g.name.toLowerCase() === gameName);
                    
                    if (game) {
                        card.addEventListener('click', () => {
                            window.open(game.link, '_blank');
                        });
                    }
                });
            }

            function setupSearch(games) {
                const searchInput = document.getElementById('search');
                
                searchInput.addEventListener('input', function() {
                    const searchTerm = this.value.toLowerCase();
                    const filteredGames = games.filter(game => 
                        game.name.toLowerCase().includes(searchTerm)
                    );
                    
                    displayGames(filteredGames);
                });
            }

            function showError() {
                document.getElementById('games-container').innerHTML = `
                    <div class="no-results">
                        Could not load games. Please try again later or check the spreadsheet URL.
                    </div>
                `;
            }
        });
    </script>
</body>
</html>
