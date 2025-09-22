<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pedro Arza - Desarrollador Web</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #e4e6ea;
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Patrón de fondo animado */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(45deg, transparent 40%, rgba(64, 123, 255, 0.02) 50%, transparent 60%),
                linear-gradient(-45deg, transparent 40%, rgba(64, 123, 255, 0.02) 50%, transparent 60%);
            background-size: 60px 60px;
            animation: movePattern 20s linear infinite;
            pointer-events: none;
            z-index: -1;
        }

        @keyframes movePattern {
            0% { transform: translate(0, 0); }
            100% { transform: translate(60px, 60px); }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: rgba(15, 15, 35, 0.95);
            backdrop-filter: blur(20px);
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            border-bottom: 1px solid rgba(64, 123, 255, 0.2);
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            background: rgba(255, 255, 255, 0.05);
            padding: 10px 20px;
            border-radius: 50px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .nav-links a {
            text-decoration: none;
            color: #e4e6ea;
            font-weight: 500;
            transition: all 0.3s;
            padding: 8px 16px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-links a:hover {
            color: #667eea;
            background: rgba(102, 126, 234, 0.1);
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
        }

        .hero-content {
            z-index: 2;
            max-width: 800px;
        }

        .hero-greeting {
            font-size: 1.2rem;
            color: #667eea;
            margin-bottom: 1rem;
            opacity: 0.9;
        }

        .hero-content h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            background: linear-gradient(135deg, #667eea, #764ba2, #f093fb);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: fadeInUp 1s ease;
        }

        .hero-subtitle {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            color: #a0a3bd;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .hero-description {
            font-size: 1.1rem;
            color: #8892b0;
            margin-bottom: 3rem;
            line-height: 1.7;
            animation: fadeInUp 1s ease 0.4s both;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            animation: fadeInUp 1s ease 0.6s both;
        }

        .btn-primary {
            padding: 15px 30px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s;
            border: 2px solid transparent;
            box-shadow: 0 8px 32px rgba(102, 126, 234, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 40px rgba(102, 126, 234, 0.4);
        }

        .btn-secondary {
            padding: 15px 30px;
            background: transparent;
            color: #667eea;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s;
            border: 2px solid #667eea;
        }

        .btn-secondary:hover {
            background: rgba(102, 126, 234, 0.1);
            transform: translateY(-3px);
        }

        /* Iconos flotantes */
        .floating-icons {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .floating-icon {
            position: absolute;
            font-size: 2rem;
            color: rgba(102, 126, 234, 0.3);
            animation: float 6s ease-in-out infinite;
        }

        .floating-icon:nth-child(1) { top: 20%; left: 10%; animation-delay: 0s; }
        .floating-icon:nth-child(2) { top: 30%; right: 15%; animation-delay: 1s; }
        .floating-icon:nth-child(3) { top: 60%; left: 20%; animation-delay: 2s; }
        .floating-icon:nth-child(4) { bottom: 30%; right: 25%; animation-delay: 3s; }
        .floating-icon:nth-child(5) { bottom: 20%; left: 15%; animation-delay: 4s; }
        .floating-icon:nth-child(6) { top: 40%; left: 50%; animation-delay: 5s; }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(10deg); }
        }

        /* Código decorativo */
        .code-block {
            position: absolute;
            right: 5%;
            top: 50%;
            transform: translateY(-50%);
            background: rgba(15, 15, 35, 0.9);
            border: 1px solid rgba(102, 126, 234, 0.2);
            border-radius: 10px;
            padding: 20px;
            font-family: 'Courier New', monospace;
            font-size: 0.9rem;
            color: #e4e6ea;
            backdrop-filter: blur(10px);
            max-width: 400px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        .code-line {
            margin: 5px 0;
        }

        .keyword { color: #ff6b6b; }
        .string { color: #4ecdc4; }
        .number { color: #ffe66d; }
        .comment { color: #95a5a6; }

        /* Secciones */
        section {
            padding: 6rem 0;
            position: relative;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 3rem;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 3px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            border-radius: 2px;
        }

        /* Sobre mí */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 4rem;
            align-items: center;
        }

        .about-image {
            width: 300px;
            height: 300px;
            border-radius: 20px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 4rem;
            font-weight: bold;
            margin: 0 auto;
            box-shadow: 0 20px 60px rgba(102, 126, 234, 0.3);
            position: relative;
            overflow: hidden;
        }

        .about-image::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.1), transparent);
            transform: translateX(-100%);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
            color: #a0a3bd;
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        /* Habilidades */
        .skills {
            background: rgba(15, 15, 35, 0.5);
        }

        .skills-categories {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 3rem;
            margin-top: 3rem;
        }

        .skill-category {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(102, 126, 234, 0.2);
            border-radius: 15px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: transform 0.3s;
        }

        .skill-category:hover {
            transform: translateY(-10px);
            border-color: rgba(102, 126, 234, 0.4);
        }

        .category-title {
            font-size: 1.3rem;
            color: #667eea;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .skill-tag {
            background: rgba(102, 126, 234, 0.1);
            border: 1px solid rgba(102, 126, 234, 0.3);
            color: #667eea;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9rem;
            transition: all 0.3s;
        }

        .skill-tag:hover {
            background: rgba(102, 126, 234, 0.2);
            transform: translateY(-2px);
        }

        /* Proyectos */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(102, 126, 234, 0.2);
            border-radius: 15px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(135deg, #667eea, #764ba2);
        }

        .project-card:hover {
            transform: translateY(-10px);
            border-color: rgba(102, 126, 234, 0.4);
            box-shadow: 0 20px 60px rgba(102, 126, 234, 0.2);
        }

        .project-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .project-card h3 {
            color: #e4e6ea;
            font-size: 1.3rem;
            margin-bottom: 1rem;
        }

        .project-card p {
            color: #a0a3bd;
            margin-bottom: 1.5rem;
            line-height: 1.6;
        }

        .project-link {
            color: #667eea;
            text-decoration: none;
            font-weight: 600;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            transition: all 0.3s;
        }

        .project-link:hover {
            gap: 12px;
        }

        /* Timeline de experiencia */
        .timeline {
            position: relative;
            max-width: 800px;
            margin: 3rem auto;
        }

        .timeline::after {
            content: '';
            position: absolute;
            width: 3px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            top: 0;
            bottom: 0;
            left: 50%;
            margin-left: -1.5px;
        }

        .timeline-item {
            padding: 20px 40px;
            position: relative;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(102, 126, 234, 0.2);
            width: 50%;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            margin-bottom: 2rem;
        }

        .timeline-item::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            background: #667eea;
            border: 3px solid rgba(15, 15, 35, 1);
            top: 25px;
            border-radius: 50%;
            z-index: 1;
        }

        .timeline-item:nth-child(odd) {
            left: 0;
        }

        .timeline-item:nth-child(odd)::after {
            right: -11px;
        }

        .timeline-item:nth-child(even) {
            left: 50%;
        }

        .timeline-item:nth-child(even)::after {
            left: -11px;
        }

        .timeline-year {
            color: #667eea;
            font-weight: bold;
            font-size: 1.1rem;
            margin-bottom: 0.5rem;
        }

        .timeline-title {
            color: #e4e6ea;
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
        }

        .timeline-company {
            color: #a0a3bd;
            font-style: italic;
            margin-bottom: 1rem;
        }

        .timeline-description {
            color: #8892b0;
            line-height: 1.6;
        }

        /* Contacto */
        .contact {
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 100%);
            text-align: center;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .contact-item {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(102, 126, 234, 0.2);
            border-radius: 15px;
            padding: 2rem;
            backdrop-filter: blur(10px);
            transition: all 0.3s;
        }

        .contact-item:hover {
            transform: translateY(-10px);
            border-color: rgba(102, 126, 234, 0.4);
        }

        .contact-icon {
            font-size: 2.5rem;
            color: #667eea;
            margin-bottom: 1rem;
        }

        .contact-item h4 {
            color: #e4e6ea;
            margin-bottom: 0.5rem;
        }

        .contact-item p {
            color: #a0a3bd;
        }

        /* Footer */
        footer {
            background: rgba(15, 15, 35, 0.9);
            color: #8892b0;
            text-align: center;
            padding: 2rem 0;
            border-top: 1px solid rgba(102, 126, 234, 0.2);
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .hero-content h1 {
                font-size: 2.5rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .code-block {
                display: none;
            }

            .timeline::after {
                left: 20px;
            }

            .timeline-item {
                width: 100%;
                left: 40px !important;
            }

            .timeline-item::after {
                left: -9px !important;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav class="container">
            <div class="logo">Pedro.dev</div>
            <ul class="nav-links">
                <li><a href="#inicio"><i class="fas fa-home"></i> Inicio</a></li>
                <li><a href="#sobre-mi"><i class="fas fa-user"></i> Sobre Mí</a></li>
                <li><a href="#proyectos"><i class="fas fa-code"></i> Proyectos</a></li>
                <li><a href="#habilidades"><i class="fas fa-tools"></i> Habilidades</a></li>
                <li><a href="#experiencia"><i class="fas fa-briefcase"></i> Experiencia</a></li>
                <li><a href="#contacto"><i class="fas fa-envelope"></i> Contacto</a></li>
            </ul>
        </nav>
    </header>

    <section id="inicio" class="hero">
        <div class="floating-icons">
            <div class="floating-icon"><i class="fab fa-js-square"></i></div>
            <div class="floating-icon"><i class="fab fa-html5"></i></div>
            <div class="floating-icon"><i class="fab fa-css3-alt"></i></div>
            <div class="floating-icon"><i class="fab fa-react"></i></div>
            <div class="floating-icon"><i class="fab fa-github"></i></div>
            <div class="floating-icon"><i class="fas fa-code"></i></div>
        </div>
        
        <div class="hero-content">
            <div class="hero-greeting">💫 Construyamos Juntos</div>
            <h1>Hola, Soy Pedro Arza</h1>
            <p class="hero-subtitle">Desarrollador Web Frontend</p>
            <p class="hero-description">
                Desarrollador web apasionado por crear experiencias digitales únicas e interactivas. 
                Me especializo en el desarrollo frontend y disfruto transformando ideas creativas 
                en realidades web funcionales y atractivas.
            </p>
            <div class="hero-buttons">
                <a href="#proyectos" class="btn-primary">Ver Proyectos</a>
                <a href="#contacto" class="btn-secondary">Contactar</a>
            </div>
        </div>

        <div class="code-block">
            <div class="code-line"><span class="keyword">const</span> <span class="string">developer</span> = {</div>
            <div class="code-line">  name: <span class="string">'Pedro Arza'</span>,</div>
            <div class="code-line">  role: <span class="string">'Frontend Developer'</span>,</div>
            <div class="code-line">  skills: [</div>
            <div class="code-line">    <span class="string">'JavaScript'</span>, <span class="string">'HTML5'</span>,</div>
            <div class="code-line">    <span class="string">'CSS3'</span>, <span class="string">'React'</span></div>
            <div class="code-line">  ],</div>
            <div class="code-line">  experience: <span class="number">2</span>,</div>
            <div class="code-line">  passion: <span class="string">'Gaming & Web'</span>,</div>
            <div class="code-line">  available: <span class="keyword">true</span></div>
            <div class="code-line">};</div>
        </div>
    </section>

    <section id="sobre-mi">
        <div class="container">
            <h2 class="section-title">Sobre Mí</h2>
            <div class="about-content">
                <div class="about-image">
                    PA
                </div>
                <div class="about-text">
                    <p>¡Hola! Soy Pedro Arza, un desarrollador web frontend apasionado por crear experiencias digitales que no solo se vean increíbles, sino que también funcionen a la perfección.</p>
                    
                    <p>Mi viaje en el desarrollo web comenzó con la curiosidad de entender cómo funcionan las páginas web, y desde entonces he estado creando proyectos que van desde juegos interactivos hasta sitios web comerciales modernos.</p>

                    <p>Me encanta el desafío de convertir ideas complejas en interfaces simples e intuitivas, siempre buscando la mejor experiencia para el usuario final.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="habilidades" class="skills">
        <div class="container">
            <h2 class="section-title">Mis Habilidades</h2>
            <div class="skills-categories">
                <div class="skill-category">
                    <h3 class="category-title">
                        <i class="fas fa-code"></i>
                        Frontend Development
                    </h3>
                    <div class="skill-tags">
                        <span class="skill-tag">HTML5</span>
                        <span class="skill-tag">CSS3</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">React</span>
                        <span class="skill-tag">Responsive Design</span>
                    </div>
                </div>
                
                <div class="skill-category">
                    <h3 class="category-title">
                        <i class="fas fa-gamepad"></i>
                        Game Development
                    </h3>
                    <div class="skill-tags">
                        <span class="skill-tag">JavaScript Games</span>
                        <span class="skill-tag">Canvas API</span>
                        <span class="skill-tag">Game Logic</span>
                        <span class="skill-tag">Interactive UI</span>
                    </div>
                </div>
                
                <div class="skill-category">
                    <h3 class="category-title">
                        <i class="fas fa-tools"></i>
                        Herramientas & Otros
                    </h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Git & GitHub</span>
                        <span class="skill-tag">VS Code</span>
                        <span class="skill-tag">UI/UX Design</span>
                        <span class="skill-tag">Web Performance</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="proyectos">
        <div class="container">
            <h2 class="section-title">Mis Proyectos</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-icon">🐍</div>
                    <h3>Snake Game</h3>
                    <p>Una versión moderna y responsive del clásico juego Snake. Desarrollado con JavaScript vanilla, incluye sistema de puntuación, efectos sonoros y controles adaptables para móvil y escritorio.</p>
                    <a href="#" class="project-link">Ver Proyecto <i class="fas fa-arrow-right"></i></a>
                </div>

                <div class="project-card">
                    <div class="project-icon">🛒</div>
                    <h3>E-commerce Site</h3>
                    <p>Página web de comercio electrónico completamente funcional con catálogo de productos, carrito de compras, sistema de filtros y diseño responsive. Interfaz moderna y user-friendly.</p>
                    <a href="#" class="project-link">Ver Proyecto <i class="fas fa-arrow-right"></i></a>
                </div>

                <div class="project-card">
                    <div class="project-icon">🚀</div>
                    <h3>Próximos Proyectos</h3>
                    <p>Actualmente desarrollando una aplicación web interactiva con React y trabajando en nuevos juegos web. ¡Pronto tendré más proyectos emocionantes que mostrar!</p>
                    <a href="#contacto" class="project-link">Hablemos <i class="fas fa-arrow-right"></i></a>
                </div>
            </div>
        </div>
    </section>

    <section id="experiencia">
        <div class="container">
            <h2 class="section-title">Mi Experiencia</h2>
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-year">2024 - Presente</div>
                    <h3 class="timeline-title">Desarrollador Frontend</h3>
                    <p class="timeline-company">Proyectos Independientes</p>
                    <p class="timeline-description">
                        Desarrollo de aplicaciones web modernas y juegos interactivos. 
                        Enfoque en crear experiencias de usuario excepcionales con tecnologías frontend.
                    </p>
                </div>
                
                <div class="timeline-item">
                    <div class="timeline-year">2023 - 2024</div>
                    <h3 class="timeline-title">Aprendizaje Intensivo</h3>
                    <p class="timeline-company">Desarrollo Web Autodidacta</p>
                    <p class="timeline-description">
                        Dominio de HTML5, CSS3, JavaScript ES6+, frameworks modernos y 
                        mejores prácticas de desarrollo web. Creación de múltiples proyectos prácticos.
                    </p>
                </div>

                <div class="timeline-item">
                    <div class="timeline-year">2023</div>
                    <h3 class="timeline-title">Primer Proyecto</h3>
                    <p class="timeline-company">Snake Game Launch</p>
                    <p class="timeline-description">
                        Desarrollo y lanzamiento de mi primer juego web completo. 
                        Implementación de lógica de juego compleja y interfaz interactiva.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <section id="contacto" class="contact">
        <div class="container">
            <h2 class="section-title">¡Trabajemos Juntos!</h2>
            <p style="color: #a0a3bd; font-size: 1.1rem; margin-bottom: 2rem;">
                ¿Tienes una idea increíble? Me encantaría conocer más sobre tu proyecto 
                y cómo podemos crear algo extraordinario juntos.
            </p>
            <div class="contact-grid">
                <div class="contact-item">
                    <div class="contact-icon"><i class="fas fa-envelope"></i></div>
                    <h4>Email</h4>
                    <p>pedro.arza@email.com</p>
                </div>
                <div class="contact-item">
                    <div class="contact-icon"><i class="fab fa-linkedin"></i></div>
                    <h4>LinkedIn</h4>
                    <p>linkedin.com/in/pedroarza</p>
                </div>
                <div class="contact-item">
                    <div class="contact-icon"><i class="fab fa-github"></i></div>
                    <h4>GitHub</h4>
                    <p>github.com/pedroarza</p>
                </div>
            </div>
        </div>
    </section>

    <footer>
        <div class="container">
            <p>&copy; 2025 Pedro Arza. Diseñado y desarrollado con ❤️</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling
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

        // Animación de entrada
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observar elementos para animación
        document.querySelectorAll('.project-card, .skill-category, .timeline-item, .contact-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(el);
        });

        // Efecto parallax para iconos flotantes
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const parallax = document.querySelectorAll('.floating-icon');
            const speed = 0.5;

            parallax.forEach(icon => {
                const yPos = -(scrolled * speed);
                icon.style.transform = `translate3d(0, ${yPos}px, 0)`;
            });
        });
    </script>
</body>
</html>
