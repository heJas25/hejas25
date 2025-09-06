<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yasmine Harfouche - Full Stack Developer</title>
    <style>
        /* Reset et styles de base */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #0a0a1a;
            color: #f0f0f0;
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
        }
        
        /* Canvas pour les particules */
        #particles-js {
            position: fixed;
            width: 100%;
            height: 100%;
            z-index: -1;
            top: 0;
            left: 0;
        }
        
        /* Conteneur principal */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
            position: relative;
            z-index: 1;
        }
        
        /* En-tête */
        .header {
            text-align: center;
            padding: 3rem 1rem;
            position: relative;
            overflow: hidden;
            border-radius: 15px;
            background: rgba(10, 15, 30, 0.7);
            backdrop-filter: blur(10px);
            margin-bottom: 2rem;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            animation: fadeIn 1.5s ease-out;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(72, 0, 255, 0.1) 0%, transparent 70%);
            animation: rotate 30s linear infinite;
            z-index: -1;
        }
        
        .profile-img {
            width: 180px;
            height: 180px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid #36BCF7;
            box-shadow: 0 0 30px rgba(54, 188, 247, 0.5);
            margin-bottom: 1.5rem;
            transition: all 0.3s ease;
            animation: float 6s ease-in-out infinite;
        }
        
        .profile-img:hover {
            transform: scale(1.05);
            box-shadow: 0 0 40px rgba(54, 188, 247, 0.8);
        }
        
        .name {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            background: linear-gradient(45deg, #36BCF7, #9d4edd, #ff6b6b);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            animation: gradientShift 8s infinite alternate;
        }
        
        .typing-container {
            min-height: 60px;
            margin-bottom: 1.5rem;
        }
        
        /* Sections */
        .section {
            background: rgba(15, 20, 40, 0.7);
            backdrop-filter: blur(10px);
            border-radius: 15px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
            animation: slideUp 1s ease-out;
            transition: transform 0.3s ease;
        }
        
        .section:hover {
            transform: translateY(-5px);
        }
        
        .section-title {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: #36BCF7;
            display: flex;
            align-items: center;
        }
        
        .section-title::after {
            content: '';
            flex: 1;
            height: 2px;
            margin-left: 1rem;
            background: linear-gradient(90deg, #36BCF7, transparent);
        }
        
        /* Cartes de compétences */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .skill-card {
            background: rgba(25, 30, 50, 0.7);
            border-radius: 10px;
            padding: 1.5rem;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(54, 188, 247, 0.2);
        }
        
        .skill-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(54, 188, 247, 0.2);
            border-color: rgba(54, 188, 247, 0.5);
        }
        
        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            color: #36BCF7;
        }
        
        /* Statistiques */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .stat-card {
            background: rgba(25, 30, 50, 0.7);
            border-radius: 10px;
            padding: 1.5rem;
            text-align: center;
            border: 1px solid rgba(54, 188, 247, 0.2);
        }
        
        .stat-number {
            font-size: 2.5rem;
            font-weight: bold;
            background: linear-gradient(45deg, #36BCF7, #9d4edd);
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            margin-bottom: 0.5rem;
        }
        
        /* Projets */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }
        
        .project-card {
            background: rgba(25, 30, 50, 0.7);
            border-radius: 10px;
            overflow: hidden;
            transition: all 0.3s ease;
            border: 1px solid rgba(54, 188, 247, 0.2);
        }
        
        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(54, 188, 247, 0.2);
            border-color: rgba(54, 188, 247, 0.5);
        }
        
        .project-img {
            width: 100%;
            height: 180px;
            object-fit: cover;
        }
        
        .project-content {
            padding: 1.5rem;
        }
        
        /* Liens sociaux */
        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 2rem;
            flex-wrap: wrap;
        }
        
        .social-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 0.8rem 1.5rem;
            background: rgba(25, 30, 50, 0.7);
            color: #f0f0f0;
            border-radius: 50px;
            text-decoration: none;
            transition: all 0.3s ease;
            border: 1px solid rgba(54, 188, 247, 0.2);
        }
        
        .social-link:hover {
            background: rgba(54, 188, 247, 0.2);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(54, 188, 247, 0.3);
        }
        
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-15px); }
            100% { transform: translateY(0px); }
        }
        
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .name {
                font-size: 2.2rem;
            }
            
            .container {
                padding: 1rem;
            }
            
            .section {
                padding: 1.5rem;
            }
            
            .skills-grid, .stats-container, .projects-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Canvas pour les particules -->
    <div id="particles-js"></div>
    
    <div class="container">
        <!-- En-tête -->
        <header class="header">
            <img src="https://avatars.githubusercontent.com/u/yourprofile" alt="Yasmine Harfouche" class="profile-img">
            <h1 class="name">Yasmine Harfouche</h1>
            <div class="typing-container">
                <div align="center">
                    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=36BCF7&center=true&vCenter=true&width=435&lines=Full+Stack+Developer;Always+learning+new+things;Love+to+code+and+create!" alt="Typing SVG" />
                </div>
            </div>
            <div align="center">
                <img src="https://github.com/yourusername/yourusername/blob/main/assets/coding.gif" width="400" height="300" alt="Coding Animation"/>
            </div>
        </header>
        
        <!-- À propos de moi -->
        <section class="section">
            <h2 class="section-title">🚀 About Me</h2>
            <p>🔭 I'm currently working on [Your Current Project]</p>
            <p>🌱 I'm currently learning [Technology you're learning]</p>
            <p>👯 I'm looking to collaborate on Open Source Projects</p>
            <p>💬 Ask me about Web Development, Programming, or anything tech-related</p>
            <p>📫 How to reach me: yasmineharfouche0@gmail.com</p>
            <p>⚡ Fun fact: [Something interesting about you]</p>
        </section>
        
        <!-- Compétences -->
        <section class="section">
            <h2 class="section-title">🛠️ Languages and Tools</h2>
            <div align="center">
                <img src="https://skillicons.dev/icons?i=js,typescript,python,java,react,nodejs,html,css,git,github,vscode,docker,mongodb,mysql,aws,firebase&perline=8" />
            </div>
            
            <h3 style="margin-top: 2rem; color: #36BCF7;">Frontend Development</h3>
            <p align="center">
                <img src="https://img.shields.io/badge/-React-61DAFB?style=for-the-badge&logo=react&logoColor=black" />
                <img src="https://img.shields.io/badge/-Vue.js-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white" />
                <img src="https://img.shields.io/badge/-Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white" />
                <img src="https://img.shields.io/badge/-HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" />
                <img src="https://img.shields.io/badge/-CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" />
                <img src="https://img.shields.io/badge/-Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" />
            </p>
            
            <h3 style="margin-top: 2rem; color: #36BCF7;">Backend Development</h3>
            <p align="center">
                <img src="https://img.shields.io/badge/-Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white" />
                <img src="https://img.shields.io/badge/-Express.js-000000?style=for-the-badge&logo=express&logoColor=white" />
                <img src="https://img.shields.io/badge/-Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
                <img src="https://img.shields.io/badge/-Django-092E20?style=for-the-badge&logo=django&logoColor=white" />
                <img src="https://img.shields.io/badge/-Flask-000000?style=for-the-badge&logo=flask&logoColor=white" />
            </p>
            
            <h3 style="margin-top: 2rem; color: #36BCF7;">Databases & Cloud</h3>
            <p align="center">
                <img src="https://img.shields.io/badge/-MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" />
                <img src="https://img.shields.io/badge/-PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white" />
                <img src="https://img.shields.io/badge/-MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" />
                <img src="https://img.shields.io/badge/-AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white" />
                <img src="https://img.shields.io/badge/-Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" />
            </p>
        </section>
        
        <!-- Statistiques GitHub -->
        <section class="section">
            <h2 class="section-title">📊 GitHub Stats</h2>
            <div align="center">
                <img src="https://github-readme-stats.vercel.app/api?username=yourusername&show_icons=true&theme=radical&hide_border=true&count_private=true" alt="GitHub Stats" />
            </div>
            <div align="center" style="margin-top: 2rem;">
                <img src="https://github-readme-streak-stats.herokuapp.com/?user=yourusername&theme=radical&hide_border=true" alt="GitHub Streak" />
            </div>
            <div align="center" style="margin-top: 2rem;">
                <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=yourusername&theme=radical&hide_border=true&include_all_commits=true&count_private=true&layout=compact" alt="Top Languages" />
            </div>
        </section>
        
        <!-- Trophées GitHub -->
        <section class="section">
            <h2 class="section-title">🏆 GitHub Trophies</h2>
            <div align="center">
                <img src="https://github-profile-trophy.vercel.app/?username=yourusername&theme=radical&no-frame=true&no-bg=false&margin-w=4" alt="GitHub Trophies" />
            </div>
        </section>
        
        <!-- Graphique d'activité -->
        <section class="section">
            <h2 class="section-title">📈 Activity Graph</h2>
            <div align="center">
                <img src="https://github-readme-activity-graph.vercel.app/graph?username=yourusername&theme=react-dark&hide_border=true" alt="Activity Graph" />
            </div>
        </section>
        
        <!-- Projets en vedette -->
        <section class="section">
            <h2 class="section-title">🌟 Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <img src="https://via.placeholder.com/400x200/0a0a1a/36BCF7?text=Project+1" alt="Project 1" class="project-img">
                    <div class="project-content">
                        <h3>Project 1</h3>
                        <p>Description of your amazing project goes here. Explain what it does and technologies used.</p>
                        <a href="https://github.com/yourusername/project1" class="social-link" style="margin-top: 1rem;">View Project</a>
                    </div>
                </div>
                
                <div class="project-card">
                    <img src="https://via.placeholder.com/400x200/0a0a1a/36BCF7?text=Project+2" alt="Project 2" class="project-img">
                    <div class="project-content">
                        <h3>Project 2</h3>
                        <p>Description of your amazing project goes here. Explain what it does and technologies used.</p>
                        <a href="https://github.com/yourusername/project2" class="social-link" style="margin-top: 1rem;">View Project</a>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Contact -->
        <section class="section">
            <h2 class="section-title">📫 Connect with me</h2>
            <div class="social-links">
                <a href="https://linkedin.com/in/yourprofile" target="_blank" class="social-link">
                    LinkedIn
                </a>
                <a href="https://twitter.com/yourhandle" target="_blank" class="social-link">
                    Twitter
                </a>
                <a href="mailto:yasmineharfouche0@gmail.com" target="_blank" class="social-link">
                    Email
                </a>
                <a href="https://yourportfolio.com" target="_blank" class="social-link">
                    Portfolio
                </a>
            </div>
        </section>
        
        <!-- Pied de page -->
        <footer style="text-align: center; padding: 2rem; opacity: 0.7;">
            <p>⭐️ From <a href="https://github.com/yourusername" style="color: #36BCF7;">Yasmine Harfouche</a></p>
        </footer>
    </div>

    <!-- Scripts pour les particules -->
    <script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
    <script>
        // Configuration et initialisation des particules
        document.addEventListener('DOMContentLoaded', function() {
            particlesJS('particles-js', {
                "particles": {
                    "number": {
                        "value": 150,
                        "density": {
                            "enable": true,
                            "value_area": 800
                        }
                    },
                    "color": {
                        "value": "#ffffff"
                    },
                    "shape": {
                        "type": "circle",
                        "stroke": {
                            "width": 0,
                            "color": "#000000"
                        },
                        "polygon": {
                            "nb_sides": 5
                        }
                    },
                    "opacity": {
                        "value": 0.5,
                        "random": true,
                        "anim": {
                            "enable": true,
                            "speed": 1,
                            "opacity_min": 0.1,
                            "sync": false
                        }
                    },
                    "size": {
                        "value": 3,
                        "random": true,
                        "anim": {
                            "enable": true,
                            "speed": 3,
                            "size_min": 0.1,
                            "sync": false
                        }
                    },
                    "line_linked": {
                        "enable": true,
                        "distance": 150,
                        "color": "#36BCF7",
                        "opacity": 0.4,
                        "width": 1
                    },
                    "move": {
                        "enable": true,
                        "speed": 2,
                        "direction": "none",
                        "random": true,
                        "straight": false,
                        "out_mode": "out",
                        "bounce": false,
                        "attract": {
                            "enable": false,
                            "rotateX": 600,
                            "rotateY": 1200
                        }
                    }
                },
                "interactivity": {
                    "detect_on": "canvas",
                    "events": {
                        "onhover": {
                            "enable": true,
                            "mode": "grab"
                        },
                        "onclick": {
                            "enable": true,
                            "mode": "push"
                        },
                        "resize": true
                    },
                    "modes": {
                        "grab": {
                            "distance": 140,
                            "line_linked": {
                                "opacity": 1
                            }
                        },
                        "push": {
                            "particles_nb": 4
                        }
                    }
                },
                "retina_detect": true
            });
            
            // Animation d'apparition progressive des sections
            const sections = document.querySelectorAll('.section');
            sections.forEach((section, index) => {
                section.style.animationDelay = `${index * 0.2}s`;
            });
        });
    </script>
</body>
</html>
