index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alyeldeen Portfolio - Small Engineer</title>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700;900&family=Crimson+Pro:wght@300;400;500;600&family=Cormorant+Garamond:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-gold: #D4AF37;
            --secondary-gold: #F4E4C1;
            --dark-bg: #0A0E1A;
            --darker-bg: #050810;
            --card-bg: #151B2E;
            --text-light: #E8E8E8;
            --text-muted: #A8A8B3;
            --accent-blue: #2E5FFF;
            --glow-gold: rgba(212, 175, 55, 0.3);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Crimson Pro', serif;
            background-color: var(--dark-bg);
            color: var(--text-light);
            line-height: 1.7;
            overflow-x: hidden;
        }

        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
            opacity: 0.03;
            background: 
                radial-gradient(circle at 20% 50%, var(--primary-gold) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, var(--accent-blue) 0%, transparent 50%);
            animation: bgShift 15s ease-in-out infinite;
        }

        @keyframes bgShift {
            0%, 100% { transform: translate(0, 0) scale(1); }
            50% { transform: translate(30px, 30px) scale(1.1); }
        }

        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(10, 14, 26, 0.95);
            backdrop-filter: blur(20px);
            z-index: 1000;
            padding: 1.5rem 0;
            border-bottom: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.3s ease;
        }

        nav.scrolled {
            padding: 1rem 0;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 3rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: 2px;
            animation: logoGlow 3s ease-in-out infinite;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .logo:hover {
            transform: scale(1.05);
        }

        @keyframes logoGlow {
            0%, 100% { filter: drop-shadow(0 0 10px var(--glow-gold)); }
            50% { filter: drop-shadow(0 0 20px var(--glow-gold)); }
        }

        .nav-links {
            display: flex;
            gap: 3rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-light);
            text-decoration: none;
            font-size: 1.05rem;
            font-weight: 500;
            letter-spacing: 1px;
            position: relative;
            transition: all 0.3s ease;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-gold);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--primary-gold);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-links a:active {
            transform: scale(0.95);
        }

        .mobile-toggle {
            display: none;
            flex-direction: column;
            gap: 6px;
            cursor: pointer;
        }

        .mobile-toggle span {
            width: 30px;
            height: 3px;
            background: var(--primary-gold);
            transition: all 0.3s ease;
        }

        .hero {
            position: relative;
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 2rem;
            overflow: hidden;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 900px;
            animation: fadeInUp 1s ease-out;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: 6rem;
            font-weight: 900;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold), var(--primary-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            background-size: 200% auto;
            animation: gradientShift 4s ease infinite;
            letter-spacing: 3px;
            line-height: 1.1;
        }

        @keyframes gradientShift {
            0%, 100% { background-position: 0% center; }
            50% { background-position: 100% center; }
        }

        .hero .tagline {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.8rem;
            color: var(--text-muted);
            font-weight: 300;
            letter-spacing: 4px;
            text-transform: uppercase;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .hero .description {
            font-size: 1.3rem;
            color: var(--text-muted);
            margin-bottom: 3rem;
            line-height: 1.8;
            animation: fadeInUp 1s ease-out 0.6s both;
            font-weight: 300;
        }

        .hero-buttons {
            display: flex;
            gap: 2rem;
            justify-content: center;
            animation: fadeInUp 1s ease-out 0.9s both;
        }

        .btn-primary, .btn-secondary {
            padding: 1.2rem 3rem;
            font-size: 1.1rem;
            font-weight: 600;
            letter-spacing: 2px;
            text-transform: uppercase;
            text-decoration: none;
            border: none;
            cursor: pointer;
            transition: all 0.4s ease;
            position: relative;
            overflow: hidden;
            font-family: 'Crimson Pro', serif;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold));
            color: var(--darker-bg);
            box-shadow: 0 10px 40px rgba(212, 175, 55, 0.3);
        }

        .btn-primary::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s ease;
        }

        .btn-primary:hover::before {
            left: 100%;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 50px rgba(212, 175, 55, 0.5);
        }

        .btn-primary:active {
            transform: translateY(-1px);
        }

        .btn-secondary {
            background: transparent;
            color: var(--primary-gold);
            border: 2px solid var(--primary-gold);
        }

        .btn-secondary:hover {
            background: var(--primary-gold);
            color: var(--darker-bg);
            transform: translateY(-3px);
        }

        .btn-secondary:active {
            transform: translateY(-1px);
        }

        .geometric-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            overflow: hidden;
            z-index: 1;
        }

        .shape {
            position: absolute;
            border: 1px solid rgba(212, 175, 55, 0.1);
            animation: float 20s ease-in-out infinite;
        }

        .shape1 {
            width: 300px;
            height: 300px;
            top: 10%;
            left: 5%;
            border-radius: 50%;
            animation-delay: 0s;
        }

        .shape2 {
            width: 200px;
            height: 200px;
            bottom: 15%;
            right: 10%;
            transform: rotate(45deg);
            animation-delay: 2s;
        }

        .shape3 {
            width: 150px;
            height: 150px;
            top: 60%;
            left: 15%;
            border-radius: 30% 70% 70% 30% / 30% 30% 70% 70%;
            animation-delay: 4s;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-30px) rotate(10deg); }
        }

        section {
            position: relative;
            z-index: 2;
            padding: 8rem 3rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-header {
            text-align: center;
            margin-bottom: 5rem;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .section-header.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 4rem;
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: 2px;
        }

        .section-subtitle {
            font-size: 1.3rem;
            color: var(--text-muted);
            font-weight: 300;
            letter-spacing: 2px;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 5rem;
            align-items: center;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .about-content.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .about-text {
            font-size: 1.25rem;
            line-height: 2;
            color: var(--text-muted);
            font-weight: 300;
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        .about-text strong {
            color: var(--primary-gold);
            font-weight: 600;
        }

        .about-image {
            position: relative;
            height: 500px;
            background: linear-gradient(135deg, var(--card-bg), var(--darker-bg));
            border-radius: 20px;
            overflow: hidden;
            border: 2px solid rgba(212, 175, 55, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .about-image::before {
            content: 'ALI';
            font-family: 'Playfair Display', serif;
            font-size: 8rem;
            font-weight: 900;
            color: rgba(212, 175, 55, 0.05);
            position: absolute;
            transform: rotate(-5deg);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2.5rem;
        }

        .skill-card {
            background: var(--card-bg);
            padding: 3rem 2rem;
            border-radius: 15px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            text-align: center;
            transition: all 0.4s ease;
            opacity: 0;
            transform: translateY(30px);
            position: relative;
            overflow: hidden;
            cursor: pointer;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.1), transparent);
            transition: left 0.6s ease;
        }

        .skill-card:hover::before {
            left: 100%;
        }

        .skill-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary-gold);
            box-shadow: 0 20px 60px rgba(212, 175, 55, 0.2);
        }

        .skill-card:active {
            transform: translateY(-8px);
        }

        .skill-icon {
            font-size: 3.5rem;
            margin-bottom: 1.5rem;
            display: inline-block;
        }

        .skill-card h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            margin-bottom: 1rem;
            color: var(--primary-gold);
            font-weight: 600;
        }

        .skill-card p {
            color: var(--text-muted);
            font-size: 1.1rem;
            line-height: 1.7;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 3rem;
        }

        .project-card {
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.4s ease;
            opacity: 0;
            transform: translateY(30px);
            cursor: pointer;
        }

        .project-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .project-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 25px 70px rgba(212, 175, 55, 0.2);
        }

        .project-card:active {
            transform: translateY(-12px);
        }

        .project-image {
            height: 250px;
            background: linear-gradient(135deg, var(--primary-gold), var(--accent-blue));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            position: relative;
            overflow: hidden;
        }

        .project-image::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(10, 14, 26, 0.3);
        }

        .project-content {
            padding: 2.5rem;
        }

        .project-content h3 {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            margin-bottom: 1rem;
            color: var(--primary-gold);
            font-weight: 600;
        }

        .project-content p {
            color: var(--text-muted);
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
            line-height: 1.7;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.8rem;
        }

        .tag {
            padding: 0.5rem 1.2rem;
            background: rgba(212, 175, 55, 0.1);
            color: var(--primary-gold);
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 500;
            border: 1px solid rgba(212, 175, 55, 0.2);
        }

        .certificates-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 3rem;
        }

        .certificate-card {
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.4s ease;
            opacity: 0;
            transform: translateY(30px);
            cursor: pointer;
        }

        .certificate-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .certificate-card:hover {
            transform: translateY(-10px);
            border-color: var(--primary-gold);
            box-shadow: 0 20px 60px rgba(212, 175, 55, 0.2);
        }

        .certificate-card:active {
            transform: translateY(-8px);
        }

        .certificate-image {
            width: 100%;
            height: 220px;
            background: #fff;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .certificate-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .certificate-card:hover .certificate-image img {
            transform: scale(1.05);
        }

        .certificate-content {
            padding: 2rem;
        }

        .certificate-content h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            margin-bottom: 0.8rem;
            color: var(--text-light);
            font-weight: 600;
        }

        .certificate-content .issuer {
            color: var(--primary-gold);
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .certificate-content .date {
            color: var(--text-muted);
            font-size: 1rem;
        }

        .contact-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease;
        }

        .contact-content.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .contact-text {
            font-size: 1.4rem;
            color: var(--text-muted);
            margin-bottom: 3rem;
            line-height: 1.9;
            font-weight: 300;
        }

        .contact-methods {
            display: flex;
            justify-content: center;
            gap: 3rem;
            flex-wrap: wrap;
            margin-bottom: 3rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1.5rem 2.5rem;
            background: var(--card-bg);
            border-radius: 15px;
            border: 1px solid rgba(212, 175, 55, 0.1);
            transition: all 0.3s ease;
            text-decoration: none;
            color: var(--text-light);
            font-size: 1.1rem;
        }

        .contact-item:hover {
            transform: translateY(-5px);
            border-color: var(--primary-gold);
            box-shadow: 0 15px 40px rgba(212, 175, 55, 0.2);
        }

        .contact-item:active {
            transform: translateY(-3px);
        }

        .contact-icon {
            font-size: 2rem;
            color: var(--primary-gold);
        }

        footer {
            position: relative;
            z-index: 2;
            background: var(--darker-bg);
            padding: 3rem;
            text-align: center;
            border-top: 1px solid rgba(212, 175, 55, 0.1);
        }

        .footer-logo {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 1rem;
            letter-spacing: 2px;
        }

        footer p {
            color: var(--text-muted);
            font-size: 1.1rem;
            margin-top: 1rem;
        }

        .scroll-top {
            position: fixed;
            bottom: 40px;
            right: 40px;
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, var(--primary-gold), var(--secondary-gold));
            color: var(--darker-bg);
            border: none;
            border-radius: 50%;
            font-size: 1.5rem;
            cursor: pointer;
            opacity: 0;
            pointer-events: none;
            transition: all 0.3s ease;
            z-index: 999;
            box-shadow: 0 10px 30px rgba(212, 175, 55, 0.3);
        }

        .scroll-top.visible {
            opacity: 1;
            pointer-events: all;
        }

        .scroll-top:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(212, 175, 55, 0.5);
        }

        .scroll-top:active {
            transform: translateY(-3px);
        }

        @media (max-width: 1024px) {
            .hero h1 {
                font-size: 4.5rem;
            }

            .section-title {
                font-size: 3rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                gap: 3rem;
            }

            .about-image {
                height: 350px;
            }
        }

        @media (max-width: 768px) {
            .nav-container {
                padding: 0 2rem;
            }

            .nav-links {
                position: fixed;
                top: 80px;
                left: -100%;
                width: 100%;
                height: calc(100vh - 80px);
                background: rgba(10, 14, 26, 0.98);
                backdrop-filter: blur(20px);
                flex-direction: column;
                align-items: center;
                justify-content: center;
                gap: 2rem;
                transition: left 0.4s ease;
            }

            .nav-links.active {
                left: 0;
            }

            .mobile-toggle {
                display: flex;
            }

            .mobile-toggle.active span:nth-child(1) {
                transform: rotate(45deg) translate(8px, 8px);
            }

            .mobile-toggle.active span:nth-child(2) {
                opacity: 0;
            }

            .mobile-toggle.active span:nth-child(3) {
                transform: rotate(-45deg) translate(8px, -8px);
            }

            .hero h1 {
                font-size: 3.5rem;
            }

            .hero .tagline {
                font-size: 1.3rem;
            }

            .hero .description {
                font-size: 1.1rem;
            }

            .hero-buttons {
                flex-direction: column;
                gap: 1.5rem;
            }

            section {
                padding: 5rem 2rem;
            }

            .section-title {
                font-size: 2.5rem;
            }

            .about-text {
                font-size: 1.1rem;
            }

            .projects-grid,
            .skills-grid,
            .certificates-grid {
                grid-template-columns: 1fr;
            }

            .contact-methods {
                flex-direction: column;
                gap: 1.5rem;
            }
        }

        @media (max-width: 480px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .logo {
                font-size: 1.4rem;
            }

            .btn-primary, .btn-secondary {
                padding: 1rem 2rem;
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>

    <nav id="navbar">
        <div class="nav-container">
            <div class="logo" onclick="scrollToSection('home')">Alyeldeen Portfolio</div>
            <ul class="nav-links" id="navLinks">
                <li><a href="#home" onclick="playClick()">Home</a></li>
                <li><a href="#about" onclick="playClick()">About</a></li>
                <li><a href="#skills" onclick="playClick()">Skills</a></li>
                <li><a href="#projects" onclick="playClick()">Projects</a></li>
                <li><a href="#certificates" onclick="playClick()">Certificates</a></li>
                <li><a href="#contact" onclick="playClick()">Contact</a></li>
            </ul>
            <div class="mobile-toggle" id="mobileToggle" onclick="playClick()">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </div>
    </nav>

    <section id="home" class="hero">
        <div class="geometric-shapes">
            <div class="shape shape1"></div>
            <div class="shape shape2"></div>
            <div class="shape shape3"></div>
        </div>
        <div class="hero-content">
            <h1>Alyeldeen</h1>
            <p class="tagline">Small Engineer</p>
            <p class="description">
                A 14-year-old Egyptian passionate about Computer Science, Analytics, and Programming. 
                Exploring the world of AI, Data Analysis, and Cloud Computing with curiosity and dedication.
            </p>
            <div class="hero-buttons">
                <a href="#contact" class="btn-primary" onclick="playClick()">Get In Touch</a>
                <a href="https://www.linkedin.com/in/ali-aboelneel-053082382" target="_blank" class="btn-secondary" onclick="playClick()">View LinkedIn</a>
            </div>
        </div>
    </section>

    <section id="about">
        <div class="section-header">
            <h2 class="section-title">About Me</h2>
            <p class="section-subtitle">Young tech enthusiast from Egypt</p>
        </div>
        <div class="about-content">
            <div class="about-text">
                <p>
                    Hi! I'm <strong>Ali Aboelneel</strong> (Alyeldeen), a <strong>14-year-old Egyptian boy</strong> 
                    with a deep passion for <strong>Computer Science, Analytics, and Programming</strong>. 
                    My journey into technology started at a young age, driven by curiosity about how things work 
                    and a desire to create innovative solutions.
                </p>
                <p>
                    I'm particularly interested in <strong>Artificial Intelligence</strong>, <strong>Data Analysis</strong>, 
                    and <strong>Cloud Computing</strong>. Through continuous learning and hands-on projects, I'm building 
                    a strong foundation in programming languages like <strong>Python</strong> and developing skills in 
                    <strong>Flutter</strong> for mobile app development.
                </p>
                <p>
                    Every day is an opportunity to learn something new, tackle challenging problems, and grow as a developer. 
                    I'm excited about the future of technology and committed to being part of it!
                </p>
            </div>
            <div class="about-image"></div>
        </div>
    </section>

    <section id="skills">
        <div class="section-header">
            <h2 class="section-title">Technical Skills</h2>
            <p class="section-subtitle">Building expertise in modern technologies</p>
        </div>
        <div class="skills-grid">
            <div class="skill-card" onclick="playClick()">
                <div class="skill-icon">🐍</div>
                <h3>Python</h3>
                <p>Programming with Python for automation, data analysis, and building intelligent applications.</p>
            </div>
            <div class="skill-card" onclick="playClick()">
                <div class="skill-icon">📊</div>
                <h3>Data Analysis</h3>
                <p>Analyzing and visualizing data to extract meaningful insights and make informed decisions.</p>
            </div>
            <div class="skill-card" onclick="playClick()">
                <div class="skill-icon">🤖</div>
                <h3>AI Basics</h3>
                <p>Learning artificial intelligence fundamentals and exploring machine learning applications.</p>
            </div>
            <div class="skill-card" onclick="playClick()">
                <div class="skill-icon">📱</div>
                <h3>Flutter</h3>
                <p>Building beautiful cross-platform mobile applications with Flutter framework.</p>
            </div>
            <div class="skill-card" onclick="playClick()">
                <div class="skill-icon">☁️</div>
                <h3>Cloud Computing</h3>
                <p>Understanding cloud platforms and deploying scalable applications.</p>
            </div>
        </div>
    </section>

    <section id="projects">
        <div class="section-header">
            <h2 class="section-title">Projects</h2>
            <p class="section-subtitle">Building and learning through practice</p>
        </div>
        <div class="projects-grid">
            <div class="project-card" onclick="playClick()">
                <div class="project-image">💡</div>
                <div class="project-content">
                    <h3>Data Analysis Projects</h3>
                    <p>
                        Exploring datasets and creating visualizations to understand patterns and trends 
                        using Python and data analysis libraries.
                    </p>
                    <div class="project-tags">
                        <span class="tag">Python</span>
                        <span class="tag">Data Analysis</span>
                        <span class="tag">Visualization</span>
                    </div>
                </div>
            </div>
            <div class="project-card" onclick="playClick()">
                <div class="project-image">📱</div>
                <div class="project-content">
                    <h3>Mobile Apps</h3>
                    <p>
                        Developing mobile applications using Flutter, focusing on clean design 
                        and user-friendly interfaces.
                    </p>
                    <div class="project-tags">
                        <span class="tag">Flutter</span>
                        <span class="tag">Dart</span>
                        <span class="tag">Mobile Dev</span>
                    </div>
                </div>
            </div>
            <div class="project-card" onclick="playClick()">
                <div class="project-image">🤖</div>
                <div class="project-content">
                    <h3>AI Learning</h3>
                    <p>
                        Studying machine learning concepts and implementing basic AI models 
                        to understand how intelligent systems work.
                    </p>
                    <div class="project-tags">
                        <span class="tag">AI</span>
                        <span class="tag">Machine Learning</span>
                        <span class="tag">Python</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="certificates">
        <div class="section-header">
            <h2 class="section-title">Certifications</h2>
            <p class="section-subtitle">Continuous learning and achievement</p>
        </div>
        <div class="certificates-grid">
            <div class="certificate-card" onclick="playClick()">
                <div class="certificate-image">
                    <img src="https://drive.google.com/thumbnail?id=1j6VCsZBw0SUFtJEYHrXx5_LFbHGyBIhG&sz=w1000" alt="Information Representation and Data Organization Certificate">
                </div>
                <div class="certificate-content">
                    <h3>Information Representation & Data Organization</h3>
                    <p class="issuer">Huawei ICT Academy</p>
                    <p class="date">January 2026</p>
                </div>
            </div>
            <div class="certificate-card" onclick="playClick()">
                <div class="certificate-image">
                    <img src="https://drive.google.com/thumbnail?id=1wF5BlDhVf9ABJeeiMDF4yQDLzaMKEueX&sz=w1000" alt="Data Management and Analysis Certificate">
                </div>
                <div class="certificate-content">
                    <h3>Data Management and Analysis</h3>
                    <p class="issuer">Huawei ICT Academy</p>
                    <p class="date">January 2026</p>
                </div>
            </div>
            <div class="certificate-card" onclick="playClick()">
                <div class="certificate-image">
                    <img src="https://drive.google.com/thumbnail?id=1HzxTNgk3nnJ4DwDuqxz6ZfwHb_jkiAuI&sz=w1000" alt="AI Basic Overview Certificate">
                </div>
                <div class="certificate-content">
                    <h3>AI Basic: Overview of AI</h3>
                    <p class="issuer">Huawei ICT Academy</p>
                    <p class="date">January 2026</p>
                </div>
            </div>
            <div class="certificate-card" onclick="playClick()">
                <div class="certificate-image">
                    <img src="https://drive.google.com/thumbnail?id=16bK4cXVk9wXyphA7v83hTsS_mycOF_73&sz=w1000" alt="Overview of AI Certificate">
                </div>
                <div class="certificate-content">
                    <h3>Overview of AI</h3>
                    <p class="issuer">Huawei ICT Academy</p>
                    <p class="date">January 2026</p>
                </div>
            </div>
            <div class="certificate-card" onclick="playClick()">
                <div class="certificate-image">
                    <img src="https://drive.google.com/thumbnail?id=1I-Cp4FPyGAM6fhQmNbArLfl29XIOKzyT&sz=w1000" alt="Mobile App Development Certificate">
                </div>
                <div class="certificate-content">
                    <h3>Mobile App Development - Grade 7-8</h3>
                    <p class="issuer">iSchool</p>
                    <p class="date">December 2024</p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact">
        <div class="section-header">
            <h2 class="section-title">Let's Connect</h2>
            <p class="section-subtitle">Always open to new opportunities</p>
        </div>
        <div class="contact-content">
            <p class="contact-text">
                I'm always excited to connect with fellow developers, learn from experienced professionals, 
                and explore new opportunities. Feel free to reach out!
            </p>
            <div class="contact-methods">
                <a href="mailto:ali.aboelneel@example.com" class="contact-item" onclick="playClick()">
                    <span class="contact-icon">✉️</span>
                    <span>Email Me</span>
                </a>
                <a href="https://www.linkedin.com/in/ali-aboelneel-053082382" target="_blank" class="contact-item" onclick="playClick()">
                    <span class="contact-icon">💼</span>
                    <span>LinkedIn</span>
                </a>
            </div>
        </div>
    </section>

    <footer>
        <div class="footer-logo">Alyeldeen Portfolio</div>
        <p>&copy; 2024 Ali Aboelneel. All rights reserved.</p>
    </footer>

    <button class="scroll-top" id="scrollTop" onclick="scrollToTop(); playClick();">↑</button>

    <script>
        function playClick() {
            const audioContext = new (window.AudioContext || window.webkitAudioContext)();
            const oscillator = audioContext.createOscillator();
            const gainNode = audioContext.createGain();
            
            oscillator.connect(gainNode);
            gainNode.connect(audioContext.destination);
            
            oscillator.frequency.value = 800;
            oscillator.type = 'sine';
            
            gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
            gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.1);
            
            oscillator.start(audioContext.currentTime);
            oscillator.stop(audioContext.currentTime + 0.1);
        }

        const mobileToggle = document.getElementById('mobileToggle');
        const navLinks = document.getElementById('navLinks');

        mobileToggle.addEventListener('click', () => {
            mobileToggle.classList.toggle('active');
            navLinks.classList.toggle('active');
        });

        navLinks.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => {
                mobileToggle.classList.remove('active');
                navLinks.classList.remove('active');
            });
        });

        const navbar = document.getElementById('navbar');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        const observerOptions = {
            threshold: 0.15,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.section-header, .about-content, .contact-content').forEach(el => {
            observer.observe(el);
        });

        document.querySelectorAll('.skill-card').forEach((card, index) => {
            card.style.transitionDelay = `${index * 0.1}s`;
            observer.observe(card);
        });

        document.querySelectorAll('.project-card').forEach((card, index) => {
            card.style.transitionDelay = `${index * 0.15}s`;
            observer.observe(card);
        });

        document.querySelectorAll('.certificate-card').forEach((card, index) => {
            card.style.transitionDelay = `${index * 0.1}s`;
            observer.observe(card);
        });

        const scrollTopBtn = document.getElementById('scrollTop');

        window.addEventListener('scroll', () => {
            if (window.scrollY > 500) {
                scrollTopBtn.classList.add('visible');
            } else {
                scrollTopBtn.classList.remove('visible');
            }
        });

        function scrollToTop() {
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }

        function scrollToSection(sectionId) {
            const section = document.getElementById(sectionId);
            if (section) {
                section.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
            }
        }

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        document.querySelectorAll('.btn-primary, .btn-secondary, .contact-item, .skill-card, .project-card, .certificate-card').forEach(element => {
            element.addEventListener('mouseenter', () => {
                const audioContext = new (window.AudioContext || window.webkitAudioContext)();
                const oscillator = audioContext.createOscillator();
                const gainNode = audioContext.createGain();
                
                oscillator.connect(gainNode);
                gainNode.connect(audioContext.destination);
                
                oscillator.frequency.value = 1000;
                oscillator.type = 'sine';
                
                gainNode.gain.setValueAtTime(0.1, audioContext.currentTime);
                gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + 0.05);
                
                oscillator.start(audioContext.currentTime);
                oscillator.stop(audioContext.currentTime + 0.05);
            });
        });
    </script>
</body>
</html>
