<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crow & Blocks Animation</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #0f172a, #1e293b);
            color: #f1f5f9;
            min-height: 100vh;
            padding: 20px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 50px;
            padding: 20px;
            background: rgba(15, 23, 42, 0.7);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
        }
        
        .crow-container {
            position: relative;
            width: 200px;
            height: 200px;
            margin-left: 20px;
        }
        
        .crow {
            position: absolute;
            width: 120px;
            height: 120px;
            background: url('https://i.ibb.co/3F6s7dG/crow.png') center/contain no-repeat;
            animation: fly 6s infinite ease-in-out;
            filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.3));
        }
        
        .blocks-container {
            position: relative;
            width: 350px;
            height: 250px;
            margin-right: 20px;
        }
        
        .block {
            position: absolute;
            width: 50px;
            height: 50px;
            background: rgba(39, 177, 115, 0.8);
            border: 2px solid #27B173;
            border-radius: 8px;
            box-shadow: 0 0 15px rgba(39, 177, 115, 0.5);
            animation-duration: 4s;
            animation-iteration-count: infinite;
            animation-timing-function: ease-in-out;
        }
        
        .block:nth-child(1) { top: 30px; left: 50px; animation: float1 5s infinite; }
        .block:nth-child(2) { top: 20px; left: 150px; animation: float2 6s infinite; }
        .block:nth-child(3) { top: 100px; left: 100px; animation: float3 4s infinite; }
        .block:nth-child(4) { top: 80px; left: 200px; animation: float4 7s infinite; }
        .block:nth-child(5) { top: 150px; left: 50px; animation: float5 5.5s infinite; }
        .block:nth-child(6) { top: 180px; left: 200px; animation: float6 6.5s infinite; }
        
        .content {
            background: rgba(15, 23, 42, 0.7);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            margin-bottom: 30px;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 30px;
            color: #27B173;
            text-align: center;
            text-shadow: 0 0 10px rgba(39, 177, 115, 0.5);
        }
        
        h2 {
            font-size: 2rem;
            margin: 30px 0 20px;
            color: #60a5fa;
            border-bottom: 2px solid #3b82f6;
            padding-bottom: 10px;
        }
        
        .section {
            margin-bottom: 40px;
        }
        
        p {
            font-size: 1.1rem;
            line-height: 1.7;
            margin-bottom: 15px;
        }
        
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }
        
        .project-card {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 25px;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid rgba(56, 189, 248, 0.3);
        }
        
        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
            border-color: #3b82f6;
        }
        
        .project-card h3 {
            color: #60a5fa;
            margin-bottom: 15px;
            font-size: 1.4rem;
        }
        
        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 15px;
        }
        
        .skill {
            background: rgba(39, 177, 115, 0.2);
            color: #27B173;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
            border: 1px solid rgba(39, 177, 115, 0.5);
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin: 30px 0;
        }
        
        .social-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            color: white;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            text-decoration: none;
        }
        
        .social-icon:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 25px;
            margin: 40px 0;
        }
        
        .stat-card {
            background: rgba(30, 41, 59, 0.7);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            border: 1px solid rgba(56, 189, 248, 0.3);
        }
        
        .stat-card h3 {
            color: #60a5fa;
            margin-bottom: 15px;
            font-size: 1.4rem;
        }
        
        .footer {
            text-align: center;
            padding: 20px;
            color: #94a3b8;
            font-size: 0.9rem;
            margin-top: 30px;
        }
        
        /* Animations */
        @keyframes fly {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            25% { transform: translate(-15px, -20px) rotate(-5deg); }
            50% { transform: translate(10px, 15px) rotate(3deg); }
            75% { transform: translate(5px, -15px) rotate(2deg); }
        }
        
        @keyframes float1 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(10px, 15px); }
        }
        
        @keyframes float2 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(-15px, 10px); }
        }
        
        @keyframes float3 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(5px, -15px); }
        }
        
        @keyframes float4 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(-10px, -5px); }
        }
        
        @keyframes float5 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(15px, 10px); }
        }
        
        @keyframes float6 {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(-5px, 15px); }
        }
        
        .glow {
            animation: glow 2s infinite alternate;
        }
        
        @keyframes glow {
            from { box-shadow: 0 0 5px rgba(39, 177, 115, 0.5); }
            to { box-shadow: 0 0 20px rgba(39, 177, 115, 0.8); }
        }
        
        /* Responsive design */
        @media (max-width: 900px) {
            .header {
                flex-direction: column;
                align-items: center;
                gap: 40px;
            }
            
            .crow-container, .blocks-container {
                margin: 0;
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="crow-container">
                <div class="crow"></div>
            </div>
            
            <div class="blocks-container">
                <div class="block"></div>
                <div class="block"></div>
                <div class="block"></div>
                <div class="block"></div>
                <div class="block"></div>
                <div class="block"></div>
            </div>
        </div>
        
        <div class="content">
            <h1>👋 About Me</h1>
            
            <div class="section">
                <p>I'm Almiqdad Yahya — a Sudanese physicist and aspiring researcher with a deep passion for theoretical and particle physics.</p>
                <p>After earning my BSc from the University of Khartoum, I pursue a Masters degree at Bolonga University in Italy. My work explores topics such as neutrino physics, beyond the Standard Model (BSM), and high-energy phenomena.</p>
                <p>I'm also passionate about visual, interactive science communication — making complex ideas tangible through code and design.</p>
            </div>
            
            <div class="section">
                <h2>🧠 Upcoming Projects</h2>
                <div class="projects-grid">
                    <div class="project-card glow">
                        <h3>Neutrino Detector Prototype</h3>
                        <p>Designing and building a basic physical neutrino detector to explore detection principles and potentially test it in a low-background environment.</p>
                    </div>
                    <div class="project-card glow">
                        <h3>Amplitude Calculator</h3>
                        <p>Developing a tool to compute simple quantum field theory amplitudes, starting with scalar interactions and aiming to eventually include spinor and gauge fields.</p>
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2>🚀 Top Projects</h2>
                <div class="projects-grid">
                    <div class="project-card">
                        <h3>Yukawa Force Simulation</h3>
                        <p>Developed a Python-based simulation of the strong nuclear force using the Yukawa potential. Utilized Pygame for interactive visualization.</p>
                    </div>
                    <div class="project-card">
                        <h3>N-Body Simulation</h3>
                        <p>High-performance simulation of gravitational systems using Python. Visualized results with Pygame and interactive dashboards.</p>
                    </div>
                    <div class="project-card">
                        <h3>Personal Portfolio Website</h3>
                        <p>Built with HTML, CSS, JavaScript, and GitHub Pages to showcase my work and research.</p>
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2>🛠️ Skills</h2>
                <div class="skills">
                    <span class="skill">Python</span>
                    <span class="skill">C++</span>
                    <span class="skill">JavaScript</span>
                    <span class="skill">HTML</span>
                    <span class="skill">CSS</span>
                    <span class="skill">LaTeX</span>
                    <span class="skill">Markdown</span>
                    <span class="skill">NumPy</span>
                    <span class="skill">Pandas</span>
                    <span class="skill">Matplotlib</span>
                    <span class="skill">SciPy</span>
                    <span class="skill">PyTorch</span>
                    <span class="skill">Git</span>
                    <span class="skill">Linux</span>
                    <span class="skill">Figma</span>
                    <span class="skill">Notion</span>
                    <span class="skill">GitHub Pages</span>
                    <span class="skill">Raspberry Pi</span>
                </div>
            </div>
            
            <div class="section">
                <h2>🌐 Connect with Me</h2>
                <div class="social-links">
                    <a href="https://facebook.com/isaac.migdad.1" class="social-icon" style="background: #1877F2;">f</a>
                    <a href="https://instagram.com/almiqdad.yahya" class="social-icon" style="background: #E4405F;">i</a>
                    <a href="https://twitter.com/miqdadgreeb" class="social-icon" style="background: #1DA1F2;">t</a>
                    <a href="https://youtube.com/@theoryofeverything2.0" class="social-icon" style="background: #FF0000;">y</a>
                </div>
            </div>
            
            <div class="stats-container">
                <div class="stat-card">
                    <h3>GitHub Stats</h3>
                    <div style="background: #1e293b; padding: 20px; border-radius: 10px; margin-top: 15px;">
                        <p>Commits: 427</p>
                        <p>Repositories: 24</p>
                        <p>Contributions: 1,258</p>
                    </div>
                </div>
                
                <div class="stat-card">
                    <h3>Top Languages</h3>
                    <div style="background: #1e293b; padding: 20px; border-radius: 10px; margin-top: 15px;">
                        <p>Python: 65%</p>
                        <p>JavaScript: 20%</p>
                        <p>C++: 10%</p>
                        <p>HTML/CSS: 5%</p>
                    </div>
                </div>
                
                <div class="stat-card">
                    <h3>Streak Stats</h3>
                    <div style="background: #1e293b; padding: 20px; border-radius: 10px; margin-top: 15px;">
                        <p>Current Streak: 28 days</p>
                        <p>Longest Streak: 112 days</p>
                        <p>Total Contributions: 1,258</p>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>© 2025 Almiqdad Yahya | Last updated: July 2025</p>
        </div>
    </div>
</body>
</html>
