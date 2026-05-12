<!DOCTYPE html>
<html lang="ky">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Portfolio</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
    <style>
        *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

        :root {
            --bg: #080808;
            --surface: #111111;
            --border: rgba(255,255,255,0.07);
            --gold: #c9a84c;
            --gold-light: #e8c97a;
            --white: #f5f0e8;
            --muted: rgba(245, 240, 232, 0.4);
            --red: #e63d2f;
        }

        html { scroll-behavior: smooth; }

        body {
            background-color: var(--bg);
            color: var(--white);
            font-family: 'DM Sans', sans-serif;
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* ── NOISE OVERLAY ── */
        body::before {
            content: '';
            position: fixed;
            inset: 0;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='1'/%3E%3C/svg%3E");
            opacity: 0.03;
            pointer-events: none;
            z-index: 9999;
        }

        /* ── NAV ── */
        nav {
            position: fixed;
            top: 0; left: 0; right: 0;
            z-index: 100;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 24px 48px;
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border-bottom: 1px solid var(--border);
            background: rgba(8,8,8,0.7);
        }

        .nav-logo {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1.6rem;
            letter-spacing: 4px;
            color: var(--white);
            text-decoration: none;
        }

        .nav-logo span {
            color: var(--gold);
        }

        .nav-dot {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 0.78rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--muted);
            font-weight: 300;
        }

        .nav-dot::before {
            content: '';
            width: 8px; height: 8px;
            border-radius: 50%;
            background: var(--red);
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(0.7); }
        }

        /* ── HERO ── */
        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            padding: 0 48px 80px;
            position: relative;
            overflow: hidden;
        }

        .hero-bg {
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse 60% 50% at 70% 40%, rgba(201,168,76,0.08) 0%, transparent 60%),
                radial-gradient(ellipse 40% 60% at 20% 80%, rgba(230,61,47,0.06) 0%, transparent 50%);
        }

        .hero-number {
            position: absolute;
            top: 50%;
            right: -2vw;
            transform: translateY(-50%);
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(160px, 25vw, 380px);
            color: rgba(255,255,255,0.02);
            line-height: 1;
            user-select: none;
            pointer-events: none;
        }

        .hero-tag {
            font-size: 0.75rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 24px;
            font-weight: 400;
            opacity: 0;
            animation: slideUp 0.8s 0.3s ease forwards;
        }

        .hero-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(56px, 10vw, 140px);
            line-height: 0.92;
            letter-spacing: 2px;
            text-transform: uppercase;
            opacity: 0;
            animation: slideUp 0.9s 0.5s ease forwards;
        }

        .hero-title em {
            font-style: normal;
            color: var(--gold);
            display: block;
        }

        .hero-sub {
            margin-top: 32px;
            max-width: 480px;
            font-size: 1rem;
            line-height: 1.7;
            color: var(--muted);
            font-weight: 300;
            opacity: 0;
            animation: slideUp 0.9s 0.7s ease forwards;
        }

        .hero-scroll {
            margin-top: 56px;
            display: flex;
            align-items: center;
            gap: 16px;
            color: var(--muted);
            font-size: 0.78rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            opacity: 0;
            animation: slideUp 0.9s 0.9s ease forwards;
        }

        .scroll-line {
            width: 48px;
            height: 1px;
            background: var(--gold);
        }

        @keyframes slideUp {
            from { opacity: 0; transform: translateY(40px); }
            to   { opacity: 1; transform: translateY(0); }
        }

        /* ── WORKS SECTION ── */
        .works {
            padding: 80px 48px 120px;
        }

        .section-header {
            display: flex;
            align-items: flex-end;
            justify-content: space-between;
            margin-bottom: 64px;
            padding-bottom: 24px;
            border-bottom: 1px solid var(--border);
        }

        .section-label {
            font-size: 0.72rem;
            letter-spacing: 4px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 12px;
            font-weight: 400;
        }

        .section-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(36px, 5vw, 64px);
            letter-spacing: 2px;
            line-height: 1;
        }

        .section-count {
            font-family: 'Bebas Neue', sans-serif;
            font-size: clamp(48px, 7vw, 96px);
            color: rgba(255,255,255,0.06);
            line-height: 1;
        }

        /* ── GRID ── */
        .grid {
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            gap: 24px;
        }

        .card {
            position: relative;
            background: var(--surface);
            border: 1px solid var(--border);
            border-radius: 4px;
            overflow: hidden;
            cursor: pointer;
            transition: border-color 0.4s ease, transform 0.4s ease;
        }

        .card:hover {
            border-color: var(--gold);
            transform: translateY(-4px);
        }

        /* Staggered large / small layout */
        .card:nth-child(1) { grid-column: span 7; }
        .card:nth-child(2) { grid-column: span 5; }
        .card:nth-child(3) { grid-column: span 12; }

        .card-number {
            position: absolute;
            top: 16px; left: 20px;
            font-family: 'Bebas Neue', sans-serif;
            font-size: 0.85rem;
            letter-spacing: 3px;
            color: var(--gold);
            z-index: 10;
            background: rgba(8,8,8,0.8);
            padding: 4px 10px;
            border-radius: 2px;
            backdrop-filter: blur(4px);
        }

        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%;
            height: 0;
            background: #0a0a0a;
        }

        .video-wrapper iframe {
            position: absolute;
            inset: 0;
            width: 100%;
            height: 100%;
            border: 0;
        }

        /* Third card wider → shorter video */
        .card:nth-child(3) .video-wrapper {
            padding-bottom: 40%;
        }

        .card-body {
            padding: 20px 24px 24px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-top: 1px solid var(--border);
        }

        .card-title {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1.3rem;
            letter-spacing: 2px;
            transition: color 0.3s;
        }

        .card:hover .card-title { color: var(--gold); }

        .card-meta {
            font-size: 0.72rem;
            color: var(--muted);
            letter-spacing: 2px;
            text-transform: uppercase;
            font-weight: 300;
        }

        .card-arrow {
            width: 36px; height: 36px;
            border: 1px solid var(--border);
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            color: var(--muted);
            font-size: 14px;
            transition: all 0.3s ease;
            flex-shrink: 0;
        }

        .card:hover .card-arrow {
            border-color: var(--gold);
            color: var(--gold);
            background: rgba(201,168,76,0.08);
            transform: rotate(45deg);
        }

        /* ── FOOTER ── */
        footer {
            padding: 40px 48px;
            border-top: 1px solid var(--border);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .footer-logo {
            font-family: 'Bebas Neue', sans-serif;
            font-size: 1.2rem;
            letter-spacing: 4px;
            color: var(--muted);
        }

        .footer-logo span { color: var(--gold); }

        .footer-copy {
            font-size: 0.75rem;
            color: rgba(245,240,232,0.25);
            letter-spacing: 1px;
        }

        .footer-links {
            display: flex;
            gap: 32px;
        }

        .footer-links a {
            font-size: 0.72rem;
            letter-spacing: 2px;
            text-transform: uppercase;
            color: var(--muted);
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-links a:hover { color: var(--gold); }

        /* ── DIVIDER LINE ANIMATION ── */
        .h-line {
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin: 0 48px;
            opacity: 0.3;
        }

        /* ── RESPONSIVE ── */
        @media (max-width: 900px) {
            nav { padding: 20px 24px; }
            .hero { padding: 0 24px 64px; }
            .works { padding: 64px 24px 80px; }

            .card:nth-child(1),
            .card:nth-child(2),
            .card:nth-child(3) { grid-column: span 12; }

            .card:nth-child(3) .video-wrapper { padding-bottom: 56.25%; }

            .section-header { flex-direction: column; align-items: flex-start; gap: 8px; }

            footer { flex-direction: column; gap: 24px; align-items: flex-start; }
            .footer-links { gap: 20px; }

            .h-line { margin: 0 24px; }
        }

        @media (max-width: 600px) {
            .nav-logo { font-size: 1.3rem; }
            .nav-dot { display: none; }
        }
    </style>
</head>
<body>

<!-- NAV -->
<nav>
    <a href="#" class="nav-logo">STUDIO<span>.</span></a>
    <div class="nav-dot">Иштер жарыяланды</div>
</nav>

<!-- HERO -->
<section class="hero">
    <div class="hero-bg"></div>
    <div class="hero-number">03</div>

    <p class="hero-tag">Видео монтаж · 2026</p>
    <h1 class="hero-title">
        Менин<br>
        <em>Иштерим</em>
    </h1>
    <p class="hero-sub">
        Ар бир кадр — бир окуя. Бул жерде мен жараткан профессионалдуу видео монтаждарды таба аласыз.
    </p>
    <div class="hero-scroll">
        <div class="scroll-line"></div>
        Иштерди карап чыгуу
    </div>
</section>

<div class="h-line"></div>

<!-- WORKS -->
<section class="works">
    <div class="section-header">
        <div>
            <p class="section-label">Портфолио</p>
            <h2 class="section-title">Тандалган Долбоорлор</h2>
        </div>
        <div class="section-count">03</div>
    </div>

    <div class="grid">

        <!-- Card 1 -->
        <div class="card">
            <div class="card-number">01</div>
            <div class="video-wrapper">
                <iframe
                    src="https://www.youtube.com/embed/xwAkAUdNo7c"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                    loading="lazy">
                </iframe>
            </div>
            <div class="card-body">
                <div>
                    <div class="card-title">Долбоор #1</div>
                    <div class="card-meta">Видео монтаж</div>
                </div>
                <div class="card-arrow">↗</div>
            </div>
        </div>

        <!-- Card 2 -->
        <div class="card">
            <div class="card-number">02</div>
            <div class="video-wrapper">
                <iframe
                    src="https://www.youtube.com/embed/l25UGAjnXJ4"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                    loading="lazy">
                </iframe>
            </div>
            <div class="card-body">
                <div>
                    <div class="card-title">Долбоор #2</div>
                    <div class="card-meta">Видео монтаж</div>
                </div>
                <div class="card-arrow">↗</div>
            </div>
        </div>

        <!-- Card 3 — full width -->
        <div class="card">
            <div class="card-number">03</div>
            <div class="video-wrapper">
                <iframe
                    src="https://www.youtube.com/embed/_vlhcwwrGHA"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen
                    loading="lazy">
                </iframe>
            </div>
            <div class="card-body">
                <div>
                    <div class="card-title">Долбоор #3</div>
                    <div class="card-meta">Видео монтаж</div>
                </div>
                <div class="card-arrow">↗</div>
            </div>
        </div>

    </div>
</section>

<div class="h-line"></div>

<!-- FOOTER -->
<footer>
    <div class="footer-logo">STUDIO<span>.</span></div>
    <div class="footer-copy">&copy; 2026 — Бардык укуктар корголгон</div>
    <nav class="footer-links">
        <a href="#">Байланыш</a>
        <a href="https://www.instagram.com/ramazan.tech?igsh=MXZucGh2am9keXd1MQ==">Instagram</a>
        <a href="https://www.instagram.com/ramazan.tech?igsh=MXZucGh2am9keXd1MQ==">YouTube</a>
    </nav>
</footer>

<script>
    // Intersection Observer — cards fade in on scroll
    const cards = document.querySelectorAll('.card');
    const observer = new IntersectionObserver((entries) => {
        entries.forEach((entry, i) => {
            if (entry.isIntersecting) {
                entry.target.style.animationDelay = `${i * 0.12}s`;
                entry.target.classList.add('visible');
                observer.unobserve(entry.target);
            }
        });
    }, { threshold: 0.1 });

    cards.forEach(card => {
        card.style.opacity = '0';
        card.style.transform = 'translateY(32px)';
        card.style.transition = 'opacity 0.7s ease, transform 0.7s ease, border-color 0.4s ease';
        observer.observe(card);
    });

    document.addEventListener('DOMContentLoaded', () => {});

    // Trigger visible class
    document.head.insertAdjacentHTML('beforeend', `
        <style>
            .card.visible {
                opacity: 1 !important;
                transform: translateY(0) !important;
            }
            .card:hover.visible {
                transform: translateY(-4px) !important;
            }
        </style>
    `);
</script>

</body>
</html>
