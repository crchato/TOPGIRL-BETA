<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top Girl Team Builder</title>
    <style>
        :root {
            --primary-color: #ff6b6b;
            --secondary-color: #4ecdc4;
            --accent-color: #ffe66d;
            --dark-color: #2c2c2c;
            --light-color: #f7fff7;
            --hover-color: #ff8e8e;
            --ur-color: #ffd700;
            --ssr-color: #c0c0c0;
            --skill1-color: #a9a9a9; /* Grey */
            --skill2-color: #90ee90; /* Green */
            --skill3-color: #87cefa; /* Blue */
            --skill4-color: #da70d6; /* Purple */
            --skill5-color: #ffd700; /* Gold */
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--light-color);
            color: var(--dark-color);
            line-height: 1.6;
        }

        header {
            background-color: var(--primary-color);
            color: white;
            text-align: center;
            padding: 1rem;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        nav {
            background-color: var(--dark-color);
            display: flex;
            justify-content: center;
            padding: 0.5rem;
            position: sticky;
            top: 4rem;
            z-index: 99;
        }

        nav a {
            color: white;
            text-decoration: none;
            padding: 0.5rem 1rem;
            margin: 0 0.5rem;
            border-radius: 4px;
            transition: background-color 0.3s;
        }

        nav a:hover {
            background-color: var(--primary-color);
        }

        main {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }

        section {
            margin-bottom: 3rem;
            padding: 1.5rem;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        h1, h2, h3 {
            color: var(--primary-color);
            margin-bottom: 1rem;
        }

        h2 {
            border-bottom: 2px solid var(--secondary-color);
            padding-bottom: 0.5rem;
        }

        p {
            margin-bottom: 1rem;
        }

        .character-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1rem;
        }

        .character-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            position: relative;
        }

        .character-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
        }

        .character-card.ur {
            border: 2px solid var(--ur-color);
        }

        .character-card.ssr {
            border: 2px solid var(--ssr-color);
        }

        .character-header {
            padding: 1rem;
            color: white;
            position: relative;
        }

        .ur .character-header {
            background-color: var(--ur-color);
        }

        .ssr .character-header {
            background-color: var(--ssr-color);
        }

        .character-info {
            padding: 1rem;
        }

        .character-stats {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .character-skills {
            margin-top: 1rem;
        }

        .skill {
            display: inline-block;
            padding: 0.25rem 0.5rem;
            border-radius: 4px;
            margin-right: 0.5rem;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
        }

        .skill.level1 {
            background-color: var(--skill1-color);
            color: white;
        }

        .skill.level2 {
            background-color: var(--skill2-color);
        }

        .skill.level3 {
            background-color: var(--skill3-color);
        }

        .skill.level4 {
            background-color: var(--skill4-color);
            color: white;
        }

        .skill.level5 {
            background-color: var(--skill5-color);
        }

        .type-badge {
            position: absolute;
            top: 0.5rem;
            right: 0.5rem;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            font-weight: bold;
            font-size: 0.8rem;
        }

        .ur .type-badge {
            background-color: white;
            color: var(--ur-color);
        }

        .ssr .type-badge {
            background-color: white;
            color: var(--dark-color);
        }

        .genre-badge {
            display: inline-block;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            background-color: var(--secondary-color);
            color: white;
            font-size: 0.8rem;
            margin-bottom: 0.5rem;
        }

        .position-badge {
            display: inline-block;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            background-color: var(--accent-color);
            color: var(--dark-color);
            font-size: 0.8rem;
            margin-left: 0.5rem;
        }

        .attribute-badge {
            display: inline-block;
            padding: 0.2rem 0.5rem;
            border-radius: 4px;
            background-color: var(--primary-color);
            color: white;
            font-size: 0.8rem;
            margin-left: 0.5rem;
        }

        .team-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
        }

        .team-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .team-header {
            background-color: var(--secondary-color);
            color: white;
            padding: 1rem;
            text-align: center;
        }

        .team-members {
            padding: 1rem;
        }

        .team-stats {
            background-color: var(--light-color);
            padding: 1rem;
            margin-top: 1rem;
            border-radius: 4px;
        }

        .team-member {
            display: flex;
            align-items: center;
            padding: 0.5rem;
            border-bottom: 1px solid #eee;
        }

        .team-member:last-child {
            border-bottom: none;
        }

        .member-type {
            width: 2.5rem;
            height: 2.5rem;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 1rem;
            font-weight: bold;
            color: white;
        }

        .member-type.ur {
            background-color: var(--ur-color);
        }

        .member-type.ssr {
            background-color: var(--ssr-color);
        }

        .calculator {
            padding: 2rem;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
        }

        .calculator-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
        }

        .character-selection {
            border-right: 1px solid #eee;
            padding-right: 2rem;
        }

        .team-preview {
            padding-left: 2rem;
        }

        .filter-controls {
            margin-bottom: 1.5rem;
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
        }

        .filter-group {
            margin-bottom: 1rem;
        }

        .filter-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        select, button {
            padding: 0.5rem 1rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            background-color: white;
            font-size: 1rem;
        }

        button {
            background-color: var(--primary-color);
            color: white;
            cursor: pointer;
            border: none;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: var(--hover-color);
        }

        .character-select {
            margin-bottom: 1rem;
            padding: 0.5rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            max-height: 300px;
            overflow-y: auto;
        }

        .character-option {
            padding: 0.5rem;
            margin-bottom: 0.5rem;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .character-option:hover {
            background-color: #f0f0f0;
        }

        .selected-characters {
            margin-top: 1rem;
        }

        .selected-character {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.5rem;
            background-color: #f0f0f0;
            border-radius: 4px;
            margin-bottom: 0.5rem;
        }

        .remove-character {
            color: var(--primary-color);
            cursor: pointer;
            font-weight: bold;
        }

        .team-stats-result {
            margin-top: 1.5rem;
            padding: 1rem;
            background-color: #f0f0f0;
            border-radius: 4px;
        }

        .synergy-bonus {
            margin-top: 1rem;
            padding: 0.5rem;
            background-color: var(--accent-color);
            border-radius: 4px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin: 1rem 0;
        }

        th, td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        th {
            background-color: var(--secondary-color);
            color: white;
        }

        tr:hover {
            background-color: #f5f5f5;
        }

        .skill-info {
            margin-top: 1rem;
        }

        .skill-info h3 {
            color: var(--secondary-color);
        }

        .skill-legend {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin: 1rem 0;
        }

        .skill-level {
            display: flex;
            align-items: center;
        }

        .skill-level-color {
            width: 1.5rem;
            height: 1.5rem;
            border-radius: 4px;
            margin-right: 0.5rem;
        }

        .tabs {
            display: flex;
            margin-bottom: 1rem;
        }

        .tab {
            padding: 0.5rem 1rem;
            background-color: #f0f0f0;
            cursor: pointer;
            border-radius: 4px 4px 0 0;
            margin-right: 0.25rem;
        }

        .tab.active {
            background-color: var(--secondary-color);
            color: white;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        @media (max-width: 768px) {
            .calculator-grid {
                grid-template-columns: 1fr;
            }

            .character-selection {
                border-right: none;
                padding-right: 0;
                border-bottom: 1px solid #eee;
                padding-bottom: 2rem;
                margin-bottom: 2rem;
            }

            .team-preview {
                padding-left: 0;
            }

            nav {
                flex-wrap: wrap;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Music Game Team Builder</h1>
        <p>Build the perfect musical team with optimized synergy bonuses</p>
    </header>

    <nav>
        <a href="#characters">Characters</a>
        <a href="#calculator">Team Calculator</a>
        <a href="#recommended-teams">Recommended Teams</a>
        <a href="#game-info">Game Info</a>
        <a href="#skills">Skills & Bonuses</a>
    </nav>

    <main>
        <section id="game-info">
            <h2>Game Information</h2>
            <div class="tabs">
                <div class="tab active" data-tab="basics">Basics</div>
                <div class="tab" data-tab="character-types">Character Types</div>
                <div class="tab" data-tab="synergy">Synergy Bonuses</div>
                <div class="tab" data-tab="skills">Skills</div>
            </div>

            <div class="tab-content active" id="basics-content">
                <h3>Core Game Mechanics</h3>
                <p>In this music game, you'll build a team of 5 characters with unique skills, stats, and synergies to compete and perform.</p>
                <ul>
                    <li>Characters have two main stats: <strong>Base Sing</strong> (attack) and <strong>Base Dance</strong> (defense)</li>
                    <li>Characters have different positions: Vocalist, Dancer, and Center</li>
                    <li>Characters belong to different genres and get synergy bonuses when teamed together</li>
                    <li>Characters have unique skills that enhance team performance</li>
                    <li>Teams consist of 5 characters with an optimal mix of skills and stats</li>
                </ul>
            </div>

            <div class="tab-content" id="character-types-content">
                <h3>Character Types</h3>
                <p>Characters come in two primary types:</p>
                <ul>
                    <li><strong>UR Characters</strong>: The strongest characters with max level 120</li>
                    <li><strong>SSR Characters</strong>: Strong characters but not as powerful as UR</li>
                </ul>
                <p><strong>Important Rules:</strong></p>
                <ul>
                    <li>Only 2 UR characters can be on a team at a time</li>
                    <li>UR characters can link with high-level SSR characters for additional bonuses</li>
                </ul>
            </div>

            <div class="tab-content" id="synergy-content">
                <h3>Genre Synergy Bonuses</h3>
                <p>Characters get bonuses based on genre combinations:</p>
                <ul>
                    <li><strong>3 characters of the same genre:</strong> +2% to Sing and Dance</li>
                    <li><strong>4 characters of the same genre:</strong> +4% to Sing and Dance</li>
                    <li><strong>5 characters of the same genre:</strong> +6% to Sing and Dance</li>
                </ul>
                <p>Available genres in the game:</p>
                <ul>
                    <li>R&B</li>
                    <li>ROCK</li>
                    <li>POP</li>
                    <li>EDM</li>
                    <li>HipHop</li>
                </ul>
            </div>

            <div class="tab-content" id="skills-content">
                <h3>Skills System</h3>
                <p>Skills have 5 tiers, with higher levels providing stronger effects:</p>
                <div class="skill-legend">
                    <div class="skill-level">
                        <div class="skill-level-color" style="background-color: var(--skill1-color);"></div>
                        <span>Level 1 (Grey)</span>
                    </div>
                    <div class="skill-level">
                        <div class="skill-level-color" style="background-color: var(--skill2-color);"></div>
                        <span>Level 2 (Green)</span>
                    </div>
                    <div class="skill-level">
                        <div class="skill-level-color" style="background-color: var(--skill3-color);"></div>
                        <span>Level 3 (Blue)</span>
                    </div>
                    <div class="skill-level">
                        <div class="skill-level-color" style="background-color: var(--skill4-color);"></div>
                        <span>Level 4 (Purple)</span>
                    </div>
                    <div class="skill-level">
                        <div class="skill-level-color" style="background-color: var(--skill5-color);"></div>
                        <span>Level 5 (Gold)</span>
                    </div>
                </div>
                <p>Specific skill info corrections:</p>
                <ul>
                    <li>Leilani has 50% increase to Normal Damage (not 20%)</li>
                    <li>Cindy reduces skill damage, not increases Rally Cap</li>
                </ul>
            </div>
        </section>

        <section id="calculator">
            <h2>Team Calculator</h2>
            <p>Build your optimal team and calculate synergy bonuses and total stats.</p>
            
            <div class="calculator">
                <div class="calculator-grid">
                    <div class="character-selection">
                        <h3>Select Characters</h3>
                        <div class="filter-controls">
                            <div class="filter-group">
                                <label for="genre-filter">Genre:</label>
                                <select id="genre-filter">
                                    <option value="all">All Genres</option>
                                    <option value="R&B">R&B</option>
                                    <option value="ROCK">Rock</option>
                                    <option value="POP">Pop</option>
                                    <option value="EDM">EDM</option>
                                    <option value="HipHop">Hip Hop</option>
                                </select>
                            </div>
                            
                            <div class="filter-group">
                                <label for="type-filter">Type:</label>
                                <select id="type-filter">
                                    <option value="all">All Types</option>
                                    <option value="UR">UR</option>
                                    <option value="SSR">SSR</option>
                                </select>
                            </div>
                            
                            <div class="filter-group">
                                <label for="position-filter">Position:</label>
                                <select id="position-filter">
                                    <option value="all">All Positions</option>
                                    <option value="Vocalist">Vocalist</option>
                                    <option value="Dancer">Dancer</option>
                                    <option value="Center">Center</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="character-select" id="character-selection-list">
                            <!-- Character options will be populated by JavaScript -->
                        </div>
                        
                        <h3>Selected Team (0/5)</h3>
                        <div class="selected-characters" id="selected-team">
                            <!-- Selected characters will appear here -->
                            <p id="no-characters-message">No characters selected yet. Add up to 5 characters to your team.</p>
                        </div>
                    </div>
                    
                    <div class="team-preview">
                        <h3>Team Stats</h3>
                        <div class="team-stats-result" id="team-stats">
                            <p>Base Stats:</p>
                            <ul>
                                <li>Total Sing (Attack): 0</li>
                                <li>Total Dance (Defense): 0</li>
                            </ul>
                            
                            <div class="synergy-bonus" id="synergy-info">
                                <p>Genre Synergy: None</p>
                                <p>Synergy Bonus: +0%</p>
                            </div>
                            
                            <p>Final Stats (with bonuses):</p>
                            <ul>
                                <li>Final Sing (Attack): 0</li>
                                <li>Final Dance (Defense): 0</li>
                            </ul>
                        </div>
                        
                        <div id="team-skills">
                            <h3>Team Skills</h3>
                            <ul id="skill-summary">
                                <li>No skills to display. Add characters to your team.</li>
                            </ul>
                        </div>
                        
                        <div id="team-composition-warning" style="margin-top: 1rem; color: var(--primary-color);"></div>
                        
                        <button id="reset-team" style="margin-top: 1rem;">Reset Team</button>
                    </div>
                </div>
            </div>
        </section>

        <section id="recommended-teams">
            <h2>Recommended Teams</h2>
            <div class="tabs">
                <div class="tab active" data-tab="home-teams">HOME Teams (with URs)</div>
                <div class="tab" data-tab="bali-teams">Initial Bali Teams (No URs)</div>
            </div>
            
            <div class="tab-content active" id="home-teams-content">
                <p>These teams include UR characters for maximum performance.</p>
                
                <div class="team-container">
                    <div class="team-card">
                        <div class="team-header">
                            <h3>R&B Powerhouse</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ur">UR</div>
                                <div>
                                    <strong>Marguerite</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ur">UR</div>
                                <div>
                                    <strong>Elizabeth</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Sora</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Julia</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Nova</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +6% (5 R&B characters)</p>
                            <p><strong>Total Base Sing:</strong> 51,275</p>
                            <p><strong>Total Base Dance:</strong> 40,801</p>
                            <p><strong>Final Sing:</strong> 54,352</p>
                            <p><strong>Final Dance:</strong> 43,249</p>
                            <p><strong>Key Skills:</strong> Normal DMG +50%, Skill DMG +20%, FAN CAP +10%</p>
                        </div>
                    </div>
                    
                    <div class="team-card">
                        <div class="team-header">
                            <h3>EDM Fusion</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ur">UR</div>
                                <div>
                                    <strong>Marguerite</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Kokoro</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Everly</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Alice</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Cindy</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +4% (4 EDM characters)</p>
                            <p><strong>Total Base Sing:</strong> 50,855</p>
                            <p><strong>Total Base Dance:</strong> 42,232</p>
                            <p><strong>Final Sing:</strong> 52,889</p>
                            <p><strong>Final Dance:</strong> 43,921</p>
                            <p><strong>Key Skills:</strong> Skill DMG +60%, Normal DMG +100%, Reduce Normal Attack DMG -12%</p>
                        </div>
                    </div>
                    
                    <div class="team-card">
                        <div class="team-header">
                            <h3>Mixed Elite</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ur">UR</div>
                                <div>
                                    <strong>Elizabeth</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ur">UR</div>
                                <div>
                                    <strong>Marguerite</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Leilani</strong>
                                    <div><span class="genre-badge">HipHop</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Skylar</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Aurora</strong>
                                    <div><span class="genre-badge">POP</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +0% (no genre synergy)</p>
                            <p><strong>Total Base Sing:</strong> 45,552</p>
                            <p><strong>Total Base Dance:</strong> 43,866</p>
                            <p><strong>Final Sing:</strong> 45,552</p>
                            <p><strong>Final Dance:</strong> 43,866</p>
                            <p><strong>Key Skills:</strong> Skill DMG +60%, Normal DMG +150%, NPC DMG +30%</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="tab-content" id="bali-teams-content">
                <p>These teams contain only SSR characters, ideal for Initial Bali content.</p>
                
                <div class="team-container">
                    <div class="team-card">
                        <div class="team-header">
                            <h3>R&B Harmony</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Sora</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Julia</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Nova</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Zendaya</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Raith</strong>
                                    <div><span class="genre-badge">R&B</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +6% (5 R&B characters)</p>
                            <p><strong>Total Base Sing:</strong> 48,003</p>
                            <p><strong>Total Base Dance:</strong> 53,118</p>
                            <p><strong>Final Sing:</strong> 50,883</p>
                            <p><strong>Final Dance:</strong> 56,305</p>
                            <p><strong>Key Skills:</strong> Normal DMG +150%, Skill DMG +20%, Car Speed +50%</p>
                        </div>
                    </div>
                    
                    <div class="team-card">
                        <div class="team-header">
                            <h3>EDM Masters</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Caroline</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Kokoro</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Everly</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Alice</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Sari</strong>
                                    <div><span class="genre-badge">EDM</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +6% (5 EDM characters)</p>
                            <p><strong>Total Base Sing:</strong> 50,699</p>
                            <p><strong>Total Base Dance:</strong> 45,820</p>
                            <p><strong>Final Sing:</strong> 53,741</p>
                            <p><strong>Final Dance:</strong> 48,569</p>
                            <p><strong>Key Skills:</strong> Skill DMG +40%, Normal DMG +100%, Fan Cap +10%</p>
                        </div>
                    </div>
                    
                    <div class="team-card">
                        <div class="team-header">
                            <h3>Rock Band</h3>
                        </div>
                        <div class="team-members">
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Yuuko</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Claire</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Paisley</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Skylar</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                            <div class="team-member">
                                <div class="member-type ssr">SSR</div>
                                <div>
                                    <strong>Talia</strong>
                                    <div><span class="genre-badge">ROCK</span></div>
                                </div>
                            </div>
                        </div>
                        <div class="team-stats">
                            <p><strong>Synergy:</strong> +6% (5 ROCK characters)</p>
                            <p><strong>Total Base Sing:</strong> 44,921</p>
                            <p><strong>Total Base Dance:</strong> 48,700</p>
                            <p><strong>Final Sing:</strong> 47,616</p>
                            <p><strong>Final Dance:</strong> 51,622</p>
                            <p><strong>Key Skills:</strong> Skill DMG +40%, Normal DMG +100%, Reduce Skill DMG -12%</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="characters">
            <h2>Character Database</h2>
            <div class="filter-controls">
                <div class="filter-group">
                    <label for="char-genre-filter">Genre:</label>
                    <select id="char-genre-filter">
                        <option value="all">All Genres</option>
                        <option value="R&B">R&B</option>
                        <option value="ROCK">Rock</option>
                        <option value="POP">Pop</option>
                        <option value="EDM">EDM</option>
                        <option value="HipHop">Hip Hop</option>
                    </select>
                </div>
                
                <div class="filter-group">
                    <label for="char-type-filter">Type:</label>
                    <select id="char-type-filter">
                        <option value="all">All Types</option>
                        <option value="UR">UR</option>
                        <option value="SSR">SSR</option>
                    </select>
                </div>
                
                <button id="apply-char-filter">Apply Filters</button>
                <button id="reset-char-filter">Reset Filters</button>
            </div>
            
            <div class="character-grid" id="character-grid">
                <!-- Character cards will be populated by JavaScript -->
            </div>
        </section>

        <section id="skills">
            <h2>Skills & Bonuses</h2>
            <p>Understanding the different skills and bonuses is crucial for building effective teams.</p>
            
            <div class="skill-info">
                <h3>Attack Skills</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Skill</th>
                            <th>Description</th>
                            <th>Effect</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>SKILL DM</td>
                            <td>Skill Damage</td>
                            <td>Increases damage dealt by skills</td>
                        </tr>
                        <tr>
                            <td>NORMAL DM</td>
                            <td>Normal Damage</td>
                            <td>Increases damage dealt by normal attacks</td>
                        </tr>
                        <tr>
                            <td>PLAYER DM</td>
                            <td>Player Damage</td>
                            <td>Increases damage dealt to player opponents</td>
                        </tr>
                        <tr>
                            <td>NPC DM</td>
                            <td>NPC Damage</td>
                            <td>Increases damage dealt to NPC opponents</td>
                        </tr>
                        <tr>
                            <td>DMG ATK</td>
                            <td>Damage Attack</td>
                            <td>Deals damage over time (e.g., 200/s)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <div class="skill-info">
                <h3>Defense Skills</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Skill</th>
                            <th>Description</th>
                            <th>Effect</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>REDUCE SKILL DMG</td>
                            <td>Reduce Skill Damage</td>
                            <td>Reduces skill damage received from opponents</td>
                        </tr>
                        <tr>
                            <td>REDUCE NORMAL ATTCK DMG</td>
                            <td>Reduce Normal Attack Damage</td>
                            <td>Reduces normal attack damage received from opponents</td>
                        </tr>
                        <tr>
                            <td>DMG DEF</td>
                            <td>Damage Defense</td>
                            <td>Absorbs a certain amount of damage per second</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <div class="skill-info">
                <h3>Support Skills</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Skill</th>
                            <th>Description</th>
                            <th>Effect</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>FAN CAP</td>
                            <td>Fan Capacity</td>
                            <td>Increases fan capacity and fan gain rate</td>
                        </tr>
                        <tr>
                            <td>RALLY CAP</td>
                            <td>Rally Capacity</td>
                            <td>Increases rally capacity and rally gain rate</td>
                        </tr>
                        <tr>
                            <td>CAR SPEED</td>
                            <td>Car Speed</td>
                            <td>Increases travel speed on the map</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <div class="skill-info">
                <h3>Special Skill Corrections</h3>
                <ul>
                    <li>Leilani has 50% increase to Normal Damage (not 20%)</li>
                    <li>Cindy reduces skill damage, not increases Rally Cap</li>
                </ul>
            </div>
        </section>
<section id="character-table">
    <h2>Character Table</h2>
    <p>Complete overview of all characters, color-coded by genre and type.</p>
    
    <style>
        .char-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1rem;
        }
        
        .char-table th, .char-table td {
            padding: 10px;
            text-align: left;
            border: 1px solid #ddd;
        }
        
        .char-table th {
            background-color: var(--secondary-color);
            color: white;
            position: sticky;
            top: 120px;
            z-index: 10;
        }
        
        .char-table tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        
        .char-table tr:hover {
            background-color: #f0f0f0;
        }
        
        /* Genre Colors */
        .rnb {
            border-left: 5px solid #ff6b6b;
        }
        
        .rock {
            border-left: 5px solid #4ecdc4;
        }
        
        .pop {
            border-left: 5px solid #ffe66d;
        }
        
        .edm {
            border-left: 5px solid #a374db;
        }
        
        .hiphop {
            border-left: 5px solid #66c6ba;
        }
        
        /* Type Colors */
        .ur-row {
            background-color: rgba(255, 215, 0, 0.1) !important;
        }
        
        .ur-row:hover {
            background-color: rgba(255, 215, 0, 0.2) !important;
        }
        
        .ur-badge {
            background-color: var(--ur-color);
            color: #333;
            font-weight: bold;
            padding: 2px 6px;
            border-radius: 4px;
        }
        
        .ssr-badge {
            background-color: var(--ssr-color);
            color: #333;
            font-weight: bold;
            padding: 2px 6px;
            border-radius: 4px;
        }
    </style>
    
    <table class="char-table">
    <caption>Character Table</caption>
    <thead>
        <tr>
                    <th>Character</th>
                    <th>Type</th>
                    <th>Genre</th>
                    <th>Position</th>
                    <th>Attribute</th>
                    <th>Base Sing</th>
                    <th>Base Dance</th>
                    <th>Skills</th>
                </tr>
            </thead>


<tbody>
    <!-- Header should only appear once at the top of the table, in the thead section -->
                
    <!-- R&B Characters -->
    <tr class="ur-row rnb">
        <td><strong>Marguerite</strong></td>
        <td><span class="ur-badge">UR</span></td>
        <td>R&B</td>
        <td>Vocalist</td>
        <td>Elegant</td>
        <td>11,261</td>
        <td>6,446</td>
        <td>Skill DMG +20%, Normal DMG +50%</td>
    </tr>
    <tr class="ur-row rnb">
        <td><strong>Elizabeth</strong></td>
        <td><span class="ur-badge">UR</span></td>
        <td>R&B</td>
        <td>Dancer</td>
        <td>Sexy</td>
        <td>6,446</td>
        <td>11,261</td>
        <td>Normal DMG +50%, Player DMG +20%</td>
    </tr>
    <tr class="rnb">
        <td><strong>Sora</strong></td>
        <td><span class="ssr-badge">SSR</span></td>
        <td>R&B</td>
        <td>Vocalist</td>
        <td>Cute</td>
        <td>13,513</td>
        <td>7,735</td>
        <td>Normal DMG +50%, Fan Cap +10%</td>
    </tr>
                <tr class="rnb">
                    <td><strong>Julia</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>R&B</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>11,261</td>
                    <td>6,446</td>
                    <td>Skill DMG +20%, Car Speed +75%</td>
                </tr>
                <tr class="rnb">
                    <td><strong>Nova</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>R&B</td>
                    <td>Dancer</td>
                    <td>Cute</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>Normal DMG +50%, DMG Defense 200/s</td>
                </tr>
                <tr class="rnb">
                    <td><strong>Zendaya</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>R&B</td>
                    <td>Center</td>
                    <td>Sexy</td>
                    <td>6,446</td>
                    <td>11,261</td>
                    <td>Normal DMG +50%, NPC DMG +20%, Car Speed +50%</td>
                </tr>
                <tr class="rnb">
                    <td><strong>Raith</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>R&B</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>7,735</td>
                    <td>13,513</td>
                    <td>Normal DMG +50%, Reduce Normal Attack DMG -12%</td>
                </tr>
                
                <!-- ROCK Characters -->
                <tr class="rock">
                    <td><strong>Yuuko</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>ROCK</td>
                    <td>Dancer</td>
                    <td>Elegant</td>
                    <td>7,735</td>
                    <td>13,513</td>
                    <td>Normal DMG +50%, Reduce Normal Attack DMG -12%</td>
                </tr>
                <tr class="rock">
                    <td><strong>Claire</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>ROCK</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
                <tr class="rock">
                    <td><strong>Paisley</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>ROCK</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>6,446</td>
                    <td>11,261</td>
                    <td>Reduce Skill DMG -12%, Reduce Normal Attack DMG -12%</td>
                </tr>
                <tr class="rock">
                    <td><strong>Skylar</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>ROCK</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>11,261</td>
                    <td>6,446</td>
                    <td>Skill DMG +20%, NPC DMG +30%</td>
                </tr>
                <tr class="rock">
                    <td><strong>Talia</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>ROCK</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>10,625</td>
                    <td>10,625</td>
                    <td>Normal DMG +50%, Fan Cap +10%</td>
                </tr>
                
                <!-- POP Characters -->
                <tr class="pop">
                    <td><strong>Chizuru</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>POP</td>
                    <td>Center</td>
                    <td>Sexy</td>
                    <td>10,625</td>
                    <td>10,625</td>
                    <td>Player DMG +20%, Rally Cap +10%</td>
                </tr>
                <tr class="pop">
                    <td><strong>Savannah</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>POP</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>6,446</td>
                    <td>11,261</td>
                    <td>Fan Cap +10%, DMG Attack 200/s</td>
                </tr>
                <tr class="pop">
                    <td><strong>Aurora</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>POP</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
                <tr class="pop">
                    <td><strong>Brooklyn</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>POP</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>11,261</td>
                    <td>6,446</td>
                    <td>NPC DMG +30%, DMG Defense 200/s</td>
                </tr>
                <tr class="pop">
                    <td><strong>Moana</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>POP</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>13,513</td>
                    <td>7,735</td>
                    <td>Reduce Skill DMG -12%, Reduce Normal Attack DMG -12%</td>
                </tr>
                
                <!-- EDM Characters -->
                <tr class="edm">
                    <td><strong>Caroline</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>6,446</td>
                    <td>11,261</td>
                    <td>Fan Cap +10%, DMG Attack 200/s</td>
                </tr>
                <tr class="edm">
                    <td><strong>Kokoro</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Center</td>
                    <td>Sexy</td>
                    <td>10,625</td>
                    <td>10,625</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
                <tr class="edm">
                    <td><strong>Everly</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
                <tr class="edm">
                    <td><strong>Alice</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>11,261</td>
                    <td>6,446</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
                <tr class="edm">
                    <td><strong>Cindy</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>Skill DMG +20%, Reduce Skill DMG -12%</td>
                </tr>
                <tr class="edm">
                    <td><strong>Sari</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>EDM</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>13,513</td>
                    <td>7,735</td>
                    <td>Player DMG +20%, Rally Cap +10%</td>
                </tr>
                
                <!-- HipHop Characters -->
                <tr class="hiphop">
                    <td><strong>Bella</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>HipHop</td>
                    <td>Vocalist</td>
                    <td>Elegant</td>
                    <td>11,261</td>
                    <td>6,446</td>
                    <td>Skill DMG +20%, Fan Cap +10%</td>
                </tr>
                <tr class="hiphop">
                    <td><strong>Avery</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>HipHop</td>
                    <td>Center</td>
                    <td>Sexy</td>
                    <td>6,446</td>
                    <td>11,261</td>
                    <td>Reduce Skill DMG -12%, Reduce Normal Attack DMG -12%</td>
                </tr>
                <tr class="hiphop">
                    <td><strong>Ayaka</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>HipHop</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>13,513</td>
                    <td>7,735</td>
                    <td>Reduce Skill DMG -12%, Reduce Normal Attack DMG -12%</td>
                </tr>
                <tr class="hiphop">
                    <td><strong>Audrey</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>HipHop</td>
                    <td>Center</td>
                    <td>Cute</td>
                    <td>8,854</td>
                    <td>8,854</td>
                    <td>NPC DMG +30%, Reduce Skill DMG -12%</td>
                </tr>
                <tr class="hiphop">
                    <td><strong>Leilani</strong></td>
                    <td><span class="ssr-badge">SSR</span></td>
                    <td>HipHop</td>
                    <td>Dancer</td>
                    <td>Sexy</td>
                    <td>7,735</td>
                    <td>13,513</td>
                    <td>Skill DMG +20%, Normal DMG +50%</td>
                </tr>
            </tbody>
        </table>
    </div>
</section>
</main>
    <script>
        // Character data from the Excel spreadsheet
        const characterData = [
            {
                "GENR": "R&B",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "UR",
                "GIRL": "Marguerite",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "R&B",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "UR",
                "GIRL": "Elizabeth",
                "NORMAL_DM": 0.5,
                "PLAYER_DM": 0.2,
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "R&B",
                "Attrib": "Cute",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Sora",
                "NORMAL_DM": 0.5,
                "FAN_CAP": 0.1,
                "BASE_SING": 13513,
                "BASE_DANCE": 7735
            },
            {
                "GENR": "R&B",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Julia",
                "SKILL_DM": 0.2,
                "CAR_SPEED": 0.75,
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "R&B",
                "Attrib": "Cute",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Nova",
                "NORMAL_DM": 0.5,
                "DMG_DEF": "200/s",
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "R&B",
                "Attrib": "Sexy",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Zendaya",
                "NORMAL_DM": 0.5,
                "NPC_DM": 0.2,
                "CAR_SPEED": 0.5,
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "R&B",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Raith",
                "NORMAL_DM": 0.5,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 7735,
                "BASE_DANCE": 13513
            },
            {
                "GENR": "ROCK",
                "Attrib": "Elegant",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Yuuko",
                "NORMAL_DM": 0.5,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 7735,
                "BASE_DANCE": 13513
            },
            {
                "GENR": "ROCK",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Claire",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "ROCK",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Paisley",
                "REDUCE_SKILL_DMG": -0.12,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "ROCK",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Skylar",
                "SKILL_DM": 0.2,
                "NPC_DM": 0.3,
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "ROCK",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Talia",
                "NORMAL_DM": 0.5,
                "FAN_CAP": 0.1,
                "BASE_SING": 10625,
                "BASE_DANCE": 10625
            },
            {
                "GENR": "POP",
                "Attrib": "Sexy",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Chizuru",
                "PLAYER_DM": 0.2,
                "RALLY_CAP": 0.1,
                "BASE_SING": 10625,
                "BASE_DANCE": 10625
            },
            {
                "GENR": "POP",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Savannah",
                "FAN_CAP": 0.1,
                "DMG_ATK": "200/s",
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "POP",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Aurora",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "POP",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Brooklyn",
                "NPC_DM": 0.3,
                "DMG_DEF": "200/s",
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "POP",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Moana",
                "REDUCE_SKILL_DMG": -0.12,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 13513,
                "BASE_DANCE": 7735
            },
            {
                "GENR": "EDM",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Caroline",
                "FAN_CAP": 0.1,
                "DMG_ATK": "200/s",
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "EDM",
                "Attrib": "Sexy",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Kokoro",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 10625,
                "BASE_DANCE": 10625
            },
            {
                "GENR": "EDM",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Everly",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "EDM",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Alice",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "EDM",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Cindy",
                "REDUCE_SKILL_DMG": -0.12,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "EDM",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Sari",
                "PLAYER_DM": 0.2,
                "RALLY_CAP": 0.1,
                "BASE_SING": 13513,
                "BASE_DANCE": 7735
            },
            {
                "GENR": "HipHop",
                "Attrib": "Elegant",
                "POSITION": "Vocalist",
                "TYPE": "SSR",
                "GIRL": "Bella",
                "SKILL_DM": 0.2,
                "FAN_CAP": 0.1,
                "BASE_SING": 11261,
                "BASE_DANCE": 6446
            },
            {
                "GENR": "HipHop",
                "Attrib": "Sexy",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Avery",
                "REDUCE_SKILL_DMG": -0.12,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 6446,
                "BASE_DANCE": 11261
            },
            {
                "GENR": "HipHop",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Ayaka",
                "REDUCE_SKILL_DMG": -0.12,
                "REDUCE_NORMAL_ATTCK_DMG": -0.12,
                "BASE_SING": 13513,
                "BASE_DANCE": 7735
            },
            {
                "GENR": "HipHop",
                "Attrib": "Cute",
                "POSITION": "Center",
                "TYPE": "SSR",
                "GIRL": "Audrey",
                "NPC_DM": 0.3,
                "REDUCE_SKILL_DMG": -0.12,
                "BASE_SING": 8854,
                "BASE_DANCE": 8854
            },
            {
                "GENR": "HipHop",
                "Attrib": "Sexy",
                "POSITION": "Dancer",
                "TYPE": "SSR",
                "GIRL": "Leilani",
                "SKILL_DM": 0.2,
                "NORMAL_DM": 0.5,
                "BASE_SING": 7735,
                "BASE_DANCE": 13513
            }
        ];

        // Apply Leilani's skill correction
        const leilaniIndex = characterData.findIndex(char => char.GIRL === "Leilani");
        if (leilaniIndex !== -1) {
            characterData[leilaniIndex].NORMAL_DM = 0.5; // 50% instead of 20%
        }

        // Apply Cindy's skill correction
        const cindyIndex = characterData.findIndex(char => char.GIRL === "Cindy");
        if (cindyIndex !== -1) {
            delete characterData[cindyIndex].RALLY_CAP;
            characterData[cindyIndex].REDUCE_SKILL_DMG = -0.12;
        }

        // DOM elements
        const tabs = document.querySelectorAll('.tab');
        const tabContents = document.querySelectorAll('.tab-content');
        const characterGrid = document.getElementById('character-grid');
        const characterSelectionList = document.getElementById('character-selection-list');
        const selectedTeam = document.getElementById('selected-team');
        const noCharactersMessage = document.getElementById('no-characters-message');
        const teamStats = document.getElementById('team-stats');
        const synergyInfo = document.getElementById('synergy-info');
        const skillSummary = document.getElementById('skill-summary');
        const teamCompositionWarning = document.getElementById('team-composition-warning');
        const resetTeamBtn = document.getElementById('reset-team');

        // Filters
        const genreFilter = document.getElementById('genre-filter');
        const typeFilter = document.getElementById('type-filter');
        const positionFilter = document.getElementById('position-filter');
        const charGenreFilter = document.getElementById('char-genre-filter');
        const charTypeFilter = document.getElementById('char-type-filter');
        const applyCharFilterBtn = document.getElementById('apply-char-filter');
        const resetCharFilterBtn = document.getElementById('reset-char-filter');

        // Tab functionality
        tabs.forEach(tab => {
            tab.addEventListener('click', () => {
                const tabId = tab.getAttribute('data-tab');
                
                // Deactivate all tabs
                tabs.forEach(t => t.classList.remove('active'));
                tabContents.forEach(content => content.classList.remove('active'));
                
                // Activate selected tab
                tab.classList.add('active');
                document.getElementById(`${tabId}-content`).classList.add('active');
            });
        });

        // Team state
        let currentTeam = [];
        
        // Populate character grid
        function populateCharacterGrid(characters) {
            characterGrid.innerHTML = '';
            
            characters.forEach(char => {
                const card = document.createElement('div');
                card.className = `character-card ${char.TYPE.toLowerCase()}`;
                
                const header = document.createElement('div');
                header.className = 'character-header';
                
                const typeBadge = document.createElement('div');
                typeBadge.className = 'type-badge';
                typeBadge.textContent = char.TYPE;
                
                const name = document.createElement('h3');
                name.textContent = char.GIRL;
                
                header.appendChild(name);
                header.appendChild(typeBadge);
                
                const info = document.createElement('div');
                info.className = 'character-info';
                
                const genreBadge = document.createElement('span');
                genreBadge.className = 'genre-badge';
                genreBadge.textContent = char.GENR;
                
                const posBadge = document.createElement('span');
                posBadge.className = 'position-badge';
                posBadge.textContent = char.POSITION;
                
                const attrBadge = document.createElement('span');
                attrBadge.className = 'attribute-badge';
                attrBadge.textContent = char.Attrib;
                
                const badges = document.createElement('div');
                badges.appendChild(genreBadge);
                badges.appendChild(posBadge);
                badges.appendChild(attrBadge);
                
                const stats = document.createElement('div');
                stats.className = 'character-stats';
                
                const singDiv = document.createElement('div');
                singDiv.innerHTML = `<strong>Sing:</strong> ${char.BASE_SING.toLocaleString()}`;
                
                const danceDiv = document.createElement('div');
                danceDiv.innerHTML = `<strong>Dance:</strong> ${char.BASE_DANCE.toLocaleString()}`;
                
                stats.appendChild(singDiv);
                stats.appendChild(danceDiv);
                
                const skills = document.createElement('div');
                skills.className = 'character-skills';
                skills.innerHTML = '<strong>Skills:</strong><br>';
                
                // Add skills
                for (const [key, value] of Object.entries(char)) {
                    if (key.includes('_DM') || key.includes('CAP') || key.includes('REDUCE') || key === 'DMG_ATK' || key === 'DMG_DEF' || key === 'CAR_SPEED') {
                        const skillSpan = document.createElement('span');
                        skillSpan.className = 'skill level3'; // Default to level 3
                        
                        let skillText = '';
                        if (key === 'SKILL_DM') skillText = `Skill DMG +${value * 100}%`;
                        else if (key === 'NORMAL_DM') skillText = `Normal DMG +${value * 100}%`;
                        else if (key === 'PLAYER_DM') skillText = `Player DMG +${value * 100}%`;
                        else if (key === 'NPC_DM') skillText = `NPC DMG +${value * 100}%`;
                        else if (key === 'FAN_CAP') skillText = `Fan Cap +${value * 100}%`;
                        else if (key === 'RALLY_CAP') skillText = `Rally Cap +${value * 100}%`;
                        else if (key === 'REDUCE_SKILL_DMG') skillText = `Reduce Skill DMG ${value * 100}%`;
                        else if (key === 'REDUCE_NORMAL_ATTCK_DMG') skillText = `Reduce Normal DMG ${value * 100}%`;
                        else if (key === 'DMG_ATK') skillText = `DMG Attack ${value}`;
                        else if (key === 'DMG_DEF') skillText = `DMG Defense ${value}`;
                        else if (key === 'CAR_SPEED') skillText = `Car Speed +${value * 100}%`;
                        
                        skillSpan.textContent = skillText;
                        if (skillText) {
                            skills.appendChild(skillSpan);
                            skills.appendChild(document.createElement('br'));
                        }
                    }
                }
                
                info.appendChild(badges);
                info.appendChild(stats);
                info.appendChild(skills);
                
                card.appendChild(header);
                card.appendChild(info);
                
                characterGrid.appendChild(card);
            });
        }
        
        // Populate character selection list
        function populateCharacterSelection(characters) {
            characterSelectionList.innerHTML = '';
            
            characters.forEach(char => {
                const option = document.createElement('div');
                option.className = 'character-option';
                option.dataset.name = char.GIRL;
                
                option.innerHTML = `
                    <strong>${char.GIRL}</strong> (${char.TYPE}) -
                    <span class="genre-badge" style="padding: 2px 5px; font-size: 0.8rem;">${char.GENR}</span>
                    <span class="position-badge" style="padding: 2px 5px; font-size: 0.8rem;">${char.POSITION}</span>
                `;
                
                option.addEventListener('click', () => {
                    addCharacterToTeam(char);
                });
                
                characterSelectionList.appendChild(option);
            });
        }
        
        // Add character to team
        function addCharacterToTeam(character) {
            // Check if character is already in team
            if (currentTeam.some(char => char.GIRL === character.GIRL)) {
                return;
            }
            
            // Check team size
            if (currentTeam.length >= 5) {
                teamCompositionWarning.textContent = 'Team is already full (5/5).';
                return;
            }
            
            // Check UR characters limit
            const urCharactersInTeam = currentTeam.filter(char => char.TYPE === 'UR').length;
            if (character.TYPE === 'UR' && urCharactersInTeam >= 2) {
                teamCompositionWarning.textContent = 'Maximum 2 UR characters allowed per team.';
                return;
            }
            
            // Add character to team
            currentTeam.push(character);
            updateTeamUI();
            updateTeamStats();
            
            // Clear warning
            teamCompositionWarning.textContent = '';
        }
        
        // Remove character from team
        function removeCharacterFromTeam(characterName) {
            currentTeam = currentTeam.filter(char => char.GIRL !== characterName);
            updateTeamUI();
            updateTeamStats();
            
            // Clear warning
            teamCompositionWarning.textContent = '';
        }
        
        // Update team UI
        function updateTeamUI() {
            if (currentTeam.length === 0) {
                noCharactersMessage.style.display = 'block';
                selectedTeam.innerHTML = '';
                selectedTeam.appendChild(noCharactersMessage);
            } else {
                noCharactersMessage.style.display = 'none';
                selectedTeam.innerHTML = '';
                
                currentTeam.forEach(char => {
                    const charDiv = document.createElement('div');
                    charDiv.className = 'selected-character';
                    
                    charDiv.innerHTML = `
                        <div>
                            <strong>${char.GIRL}</strong> (${char.TYPE}) - ${char.GENR}
                        </div>
                        <span class="remove-character" data-name="${char.GIRL}">×</span>
                    `;
                    
                    selectedTeam.appendChild(charDiv);
                });
                
                // Add remove event listeners
                document.querySelectorAll('.remove-character').forEach(btn => {
                    btn.addEventListener('click', (e) => {
                        const charName = e.target.dataset.name;
                        removeCharacterFromTeam(charName);
                    });
                });
            }
            
            // Update team count in header
            const teamHeader = selectedTeam.previousElementSibling;
            teamHeader.textContent = `Selected Team (${currentTeam.length}/5)`;
        }
        
        // Calculate synergy bonus
        function calculateSynergyBonus(team) {
            const genreCounts = {};
            
            team.forEach(char => {
                genreCounts[char.GENR] = (genreCounts[char.GENR] || 0) + 1;
            });
            
            let highestCount = 0;
            let highestGenre = null;
            
            for (const [genre, count] of Object.entries(genreCounts)) {
                if (count > highestCount) {
                    highestCount = count;
                    highestGenre = genre;
                }
            }
            
            let bonusPercentage = 0;
            
            if (highestCount >= 5) bonusPercentage = 6;
            else if (highestCount >= 4) bonusPercentage = 4;
            else if (highestCount >= 3) bonusPercentage = 2;
            
            return {
                genre: highestGenre,
                count: highestCount,
                percentage: bonusPercentage
            };
        }
        
        // Update team stats
        function updateTeamStats() {
            if (currentTeam.length === 0) {
                teamStats.innerHTML = `
                    <p>Base Stats:</p>
                    <ul>
                        <li>Total Sing (Attack): 0</li>
                        <li>Total Dance (Defense): 0</li>
                    </ul>
                    
                    <div class="synergy-bonus" id="synergy-info">
                        <p>Genre Synergy: None</p>
                        <p>Synergy Bonus: +0%</p>
                    </div>
                    
                    <p>Final Stats (with bonuses):</p>
                    <ul>
                        <li>Final Sing (Attack): 0</li>
                        <li>Final Dance (Defense): 0</li>
                    </ul>
                `;
                
                skillSummary.innerHTML = '<li>No skills to display. Add characters to your team.</li>';
                return;
            }
            
            // Calculate base stats
            let totalSing = 0;
            let totalDance = 0;
            
            currentTeam.forEach(char => {
                totalSing += char.BASE_SING;
                totalDance += char.BASE_DANCE;
            });
            
            // Calculate synergy bonus
            const synergy = calculateSynergyBonus(currentTeam);
            
            // Calculate final stats with bonuses
            const finalSing = totalSing * (1 + synergy.percentage / 100);
            const finalDance = totalDance * (1 + synergy.percentage / 100);
            
            // Update stats UI
            teamStats.innerHTML = `
                <p>Base Stats:</p>
                <ul>
                    <li>Total Sing (Attack): ${totalSing.toLocaleString()}</li>
                    <li>Total Dance (Defense): ${totalDance.toLocaleString()}</li>
                </ul>
                
                <div class="synergy-bonus">
                    <p>Genre Synergy: ${synergy.genre ? `${synergy.count}x ${synergy.genre}` : 'None'}</p>
                    <p>Synergy Bonus: +${synergy.percentage}%</p>
                </div>
                
                <p>Final Stats (with bonuses):</p>
                <ul>
                    <li>Final Sing (Attack): ${Math.round(finalSing).toLocaleString()}</li>
                    <li>Final Dance (Defense): ${Math.round(finalDance).toLocaleString()}</li>
                </ul>
            `;
            
            // Update skills summary
            updateSkillsSummary();
        }
        
        // Update skills summary
        function updateSkillsSummary() {
            if (currentTeam.length === 0) {
                skillSummary.innerHTML = '<li>No skills to display. Add characters to your team.</li>';
                return;
            }
            
            const skillsCount = {
                SKILL_DM: 0,
                NORMAL_DM: 0,
                PLAYER_DM: 0,
                NPC_DM: 0,
                FAN_CAP: 0,
                RALLY_CAP: 0,
                REDUCE_SKILL_DMG: 0,
                REDUCE_NORMAL_ATTCK_DMG: 0,
                DMG_ATK: 0,
                DMG_DEF: 0,
                CAR_SPEED: 0
            };
            
            currentTeam.forEach(char => {
                for (const [key, value] of Object.entries(char)) {
                    if (Object.keys(skillsCount).includes(key)) {
                        skillsCount[key] += value;
                    }
                }
            });
            
            skillSummary.innerHTML = '';
            
            for (const [skill, value] of Object.entries(skillsCount)) {
                if (value !== 0) {
                    const li = document.createElement('li');
                    
                    let skillText = '';
                    if (skill === 'SKILL_DM') skillText = `Skill DMG +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'NORMAL_DM') skillText = `Normal DMG +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'PLAYER_DM') skillText = `Player DMG +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'NPC_DM') skillText = `NPC DMG +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'FAN_CAP') skillText = `Fan Cap +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'RALLY_CAP') skillText = `Rally Cap +${(value * 100).toFixed(0)}%`;
                    else if (skill === 'REDUCE_SKILL_DMG') skillText = `Reduce Skill DMG ${(value * 100).toFixed(0)}%`;
                    else if (skill === 'REDUCE_NORMAL_ATTCK_DMG') skillText = `Reduce Normal DMG ${(value * 100).toFixed(0)}%`;
                    else if (skill === 'DMG_ATK') skillText = `DMG Attack ${value}`;
                    else if (skill === 'DMG_DEF') skillText = `DMG Defense ${value}`;
                    else if (skill === 'CAR_SPEED') skillText = `Car Speed +${(value * 100).toFixed(0)}%`;
                    
                    li.textContent = skillText;
                    skillSummary.appendChild(li);
                }
            }
            
            if (skillSummary.children.length === 0) {
                skillSummary.innerHTML = '<li>No active skills in this team.</li>';
            }
        }
        
        // Reset team
        resetTeamBtn.addEventListener('click', () => {
            currentTeam = [];
            updateTeamUI();
            updateTeamStats();
            teamCompositionWarning.textContent = '';
        });
        
        // Filter characters for selection
        function filterCharactersForSelection() {
            let filtered = [...characterData];
            
            const genre = genreFilter.value;
            const type = typeFilter.value;
            const position = positionFilter.value;
            
            if (genre !== 'all') {
                filtered = filtered.filter(char => char.GENR === genre);
            }
            
            if (type !== 'all') {
                filtered = filtered.filter(char => char.TYPE === type);
            }
            
            if (position !== 'all') {
                filtered = filtered.filter(char => char.POSITION === position);
            }
            
            return filtered;
        }
        
        // Filter characters for grid
        function filterCharactersForGrid() {
            let filtered = [...characterData];
            
            const genre = charGenreFilter.value;
            const type = charTypeFilter.value;
            
            if (genre !== 'all') {
                filtered = filtered.filter(char => char.GENR === genre);
            }
            
            if (type !== 'all') {
                filtered = filtered.filter(char => char.TYPE === type);
            }
            
            return filtered;
        }
        
        // Event listeners for filters
        genreFilter.addEventListener('change', () => {
            populateCharacterSelection(filterCharactersForSelection());
        });
        
        typeFilter.addEventListener('change', () => {
            populateCharacterSelection(filterCharactersForSelection());
        });
        
        positionFilter.addEventListener('change', () => {
            populateCharacterSelection(filterCharactersForSelection());
        });
        
        applyCharFilterBtn.addEventListener('click', () => {
            populateCharacterGrid(filterCharactersForGrid());
        });
        
        resetCharFilterBtn.addEventListener('click', () => {
            charGenreFilter.value = 'all';
            charTypeFilter.value = 'all';
            populateCharacterGrid(characterData);
        });
        
        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            populateCharacterGrid(characterData);
            populateCharacterSelection(characterData);
            updateTeamStats();
        });
    </script>
</body>
</html>
