<DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Brew & Co. | Where Every Cup Tells a Story</title>
    <meta name="description" content="Specialty coffee & handcrafted food in a warm, inviting space. Freshly roasted, artisan pastries, community events." />
    <meta name="theme-color" content="#3C2A1F" />
    <!-- Tailwind CSS + Google Fonts -->
    <script src="https://cdn.tailwindcss.com">
    </script>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
 <style>
        /*── Reset & Base ── */
        *,
        *::before,
        *::after {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        html {
            scroll-behavior: smooth;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }
        body {
            font-family: 'Inter', sans-serif;
            background: #FFF8F0;
            color: #2D1B0E;
            overflow-x: hidden;
        }
        h1,
        h2,
        h3,
        h4,
        h5,
        h6 {
            font-family: 'Playfair Display', serif;
            font-weight: 600;
            letter-spacing: -0.02em;
        }

    /* ── Color System ── */

:root {
            --cream: #FFF8F0;
            --beige: #F5F0E8;
            --warm-brown: #8B6F47;
            --muted-green: #7A9E7E;
            --dark-brown: #3C2A1F;
            --light-gold: #E8D5B7;
            --shadow-soft: 0 8px 32px rgba(60, 42, 31, 0.08);
            --shadow-glass: 0 8px 32px rgba(60, 42, 31, 0.06);
            --radius-card: 20px;
            --radius-sm: 12px;
        }

    /* ── Scrollbar ── */
::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: var(--cream);
        }
        ::-webkit-scrollbar-thumb {
            background: var(--warm-brown);
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: var(--dark-brown);
        }

    /* ── Utility Classes ── */
.font-serif {
            font-family: 'Playfair Display', serif;
        }
        .font-sans {
            font-family: 'Inter', sans-serif;
        }
        .text-balance {
            text-wrap: balance;
        }

    /* ── Scroll Progress ── */
#scroll-progress {
            position: fixed;
            top: 0;
            left: 0;
            height: 3px;
            background: linear-gradient(90deg, var(--warm-brown), var(--muted-green));
            z-index: 9999;
            width: 0%;
            transition: width 0.1s ease-out;
        }

    /* ── Navbar ── */
.navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            padding: 0.75rem 2rem;
            transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            background: rgba(255, 248, 240, 0.6);
            backdrop-filter: blur(20px) saturate(180%);
            -webkit-backdrop-filter: blur(20px) saturate(180%);
            border-bottom: 1px solid rgba(139, 111, 71, 0.08);
        }
        .navbar.scrolled {
            padding: 0.5rem 2rem;
            background: rgba(255, 248, 240, 0.92);
            box-shadow: 0 4px 30px rgba(60, 42, 31, 0.06);
        }
        .navbar .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.6rem;
            font-weight: 700;
            color: var(--dark-brown);
            text-decoration: none;
            letter-spacing: -0.03em;
            transition: opacity 0.3s;
        }
        .navbar .logo:hover {
            opacity: 0.75;
        }
        .navbar .nav-link {
            position: relative;
            font-size: 0.875rem;
            font-weight: 500;
            color: var(--dark-brown);
            text-decoration: none;
            padding: 0.25rem 0;
            transition: color 0.3s;
        }
        .navbar .nav-link::after {
            content: '';
            position: absolute;
            bottom: -2px;
            left: 0;
            width: 0;
            height: 1.5px;
            background: var(--warm-brown);
            transition: width 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .navbar .nav-link:hover::after {
            width: 100%;
        }
        .navbar .nav-link:hover {
            color: var(--warm-brown);
        }
        .navbar .cta-btn {
            background: var(--dark-brown);
            color: var(--cream);
            border: none;
            padding: 0.5rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.85rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            box-shadow: 0 4px 14px rgba(60, 42, 31, 0.15);
        }
        .navbar .cta-btn:hover {
            transform: translateY(-2px) scale(1.02);
            box-shadow: 0 8px 24px rgba(60, 42, 31, 0.2);
            background: #4D3424;
        }
        .navbar .mobile-toggle {
            display: none;
            flex-direction: column;
            gap: 5px;
            cursor: pointer;
            background: none;
            border: none;
            padding: 4px;
        }
        .navbar .mobile-toggle span {
            width: 26px;
            height: 2px;
            background: var(--dark-brown);
            border-radius: 2px;
            transition: all 0.3s;
        }
        .navbar .mobile-toggle.active span:nth-child(1) {
            transform: rotate(45deg) translate(5px, 5px);
        }
        .navbar .mobile-toggle.active span:nth-child(2) {
            opacity: 0;
        }
        .navbar .mobile-toggle.active span:nth-child(3) {
            transform: rotate(-45deg) translate(5px, -5px);
        }

@media (max-width: 768px) {
            .navbar {
                padding: 0.6rem 1.25rem;
            }
            .navbar .nav-links {
                position: fixed;
                top: 64px;
                left: 0;
                right: 0;
                background: rgba(255, 248, 240, 0.98);
                backdrop-filter: blur(20px);
                flex-direction: column;
                padding: 2rem 1.5rem;
                gap: 1.25rem;
                transform: translateY(-110%);
                opacity: 0;
                transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
                border-bottom: 1px solid rgba(139, 111, 71, 0.08);
                pointer-events: none;
                box-shadow: 0 20px 40px rgba(60, 42, 31, 0.06);
            }
            .navbar .nav-links.open {
                transform: translateY(0);
                opacity: 1;
                pointer-events: all;
            }
            .navbar .mobile-toggle {
                display: flex;
            }
            .navbar .cta-btn {
                display: none;
            }
            .navbar .nav-links .cta-btn-mobile {
                display: inline-block;
                margin-top: 0.5rem;
                background: var(--dark-brown);
                color: var(--cream);
                border: none;
                padding: 0.6rem 1.5rem;
                border-radius: 50px;
                font-weight: 600;
                font-size: 0.9rem;
                cursor: pointer;
                transition: all 0.3s;
                text-align: center;
            }
            .navbar .nav-links .cta-btn-mobile:hover {
                background: #4D3424;
                transform: translateY(-2px);
            }
        }
        @media (min-width: 769px) {
            .navbar .nav-links .cta-btn-mobile {
                display: none;
            }
        }

    /* ── Hero ── */
.hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            background: var(--dark-brown);
            padding: 8rem 2rem 6rem;
        }
        .hero-bg {
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 20% 50%, rgba(139, 111, 71, 0.4) 0%, transparent 60%),
                radial-gradient(ellipse at 80% 50%, rgba(122, 158, 126, 0.2) 0%, transparent 50%),
                url('data:image/svg+xml,%3Csvg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg"%3E%3Cfilter id="n"%3E%3CfeTurbulence type="fractalNoise" baseFrequency="0.65" numOctaves="3" stitchTiles="stitch"/%3E%3C/filter%3E%3Crect width="100%25" height="100%25" filter="url(%23n)" opacity="0.04"/%3E%3C/svg%3E');
            background-size: cover, cover, 200px 200px;
            opacity: 0.6;
        }
        .hero-bg-image {
            position: absolute;
            inset: 0;
            background-image: url('https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?q=80&w=2078&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
            background-size: cover;
            background-position: center 30%;
            background-repeat: no-repeat;
            opacity: 0.35;
            transform: scale(1.05);
            transition: transform 0.1s ease-out;
        }
        .hero-content {
            position: relative;
            z-index: 2;
            text-align: center;
            max-width: 820px;
            color: #fff;
        }
        .hero-content .badge {
            display: inline-block;
            padding: 0.35rem 1.25rem;
            border-radius: 50px;
            background: rgba(255, 248, 240, 0.12);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 248, 240, 0.15);
            font-size: 0.8rem;
            font-weight: 500;
            letter-spacing: 0.3px;
            text-transform: uppercase;
            color: var(--light-gold);
            margin-bottom: 1.5rem;
            animation: fadeInDown 0.8s ease-out forwards;
            opacity: 0;
        }
        .hero-content h1 {
            font-size: clamp(3rem, 8vw, 6.5rem);
            font-weight: 700;
            line-height: 1.05;
            letter-spacing: -0.04em;
            color: #fff;
            text-shadow: 0 2px 40px rgba(0, 0, 0, 0.15);
            animation: fadeInUp 1s ease-out 0.2s forwards;
            opacity: 0;
        }
        .hero-content h1 .highlight {
            background: linear-gradient(135deg, var(--light-gold), #F5E6CC);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .hero-content p {
            font-size: clamp(1.05rem, 2vw, 1.3rem);
            color: rgba(255, 248, 240, 0.8);
            margin: 1.5rem auto 2.5rem;
            max-width: 600px;
            font-weight: 300;
            line-height: 1.7;
            animation: fadeInUp 1s ease-out 0.4s forwards;
            opacity: 0;
        }
        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            animation: fadeInUp 1s ease-out 0.6s forwards;
            opacity: 0;
        }
        .hero-buttons .btn-primary {
            background: #fff;
            color: var(--dark-brown);
            border: none;
            padding: 0.9rem 2.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            box-shadow: 0 8px 28px rgba(0, 0, 0, 0.15);
        }
        .hero-buttons .btn-primary:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 16px 40px rgba(0, 0, 0, 0.2);
        }
        .hero-buttons .btn-secondary {
            background: transparent;
            color: #fff;
            border: 1.5px solid rgba(255, 248, 240, 0.35);
            padding: 0.9rem 2.5rem;
            border-radius: 50px;
            font-weight: 500;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            backdrop-filter: blur(4px);
        }
        .hero-buttons .btn-secondary:hover {
            background: rgba(255, 248, 240, 0.1);
            border-color: rgba(255, 248, 240, 0.6);
            transform: translateY(-3px);
        }

.hero-scroll-indicator {
            position: absolute;
            bottom: 2.5rem;
            left: 50%;
            transform: translateX(-50%);
            z-index: 2;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
            color: rgba(255, 248, 240, 0.5);
            font-size: 0.7rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            animation: fadeIn 1.5s ease-out 1.2s forwards, floatY 3s ease-in-out infinite 2s;
            opacity: 0;
        }
        .hero-scroll-indicator .scroll-line {
            width: 1px;
            height: 40px;
            background: linear-gradient(to bottom, rgba(255, 248, 240, 0.3), transparent);
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
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        @keyframes floatY {
            0%,
            100% {
                transform: translateX(-50%) translateY(0);
            }
            50% {
                transform: translateX(-50%) translateY(8px);
            }
        }

    /* ── Section Common ── */
.section {
            padding: 6rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }
        .section-label {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: var(--warm-brown);
            font-weight: 600;
            margin-bottom: 1rem;
        }
        .section-title {
            font-size: clamp(2.2rem, 5vw, 3.5rem);
            font-weight: 700;
            color: var(--dark-brown);
            line-height: 1.1;
            margin-bottom: 1.25rem;
        }
        .section-subtitle {
            font-size: 1.05rem;
            color: #7A6B5D;
            max-width: 600px;
            line-height: 1.7;
            font-weight: 300;
        }

    /* ── Reveal Animations ── */
.reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: all 0.85s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .reveal-left {
            opacity: 0;
            transform: translateX(-50px);
            transition: all 0.85s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .reveal-left.visible {
            opacity: 1;
            transform: translateX(0);
        }
        .reveal-right {
            opacity: 0;
            transform: translateX(50px);
            transition: all 0.85s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .reveal-right.visible {
            opacity: 1;
            transform: translateX(0);
        }
        .reveal-scale {
            opacity: 0;
            transform: scale(0.92);
            transition: all 0.85s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .reveal-scale.visible {
            opacity: 1;
            transform: scale(1);
        }
        .stagger-item {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .stagger-item.visible {
            opacity: 1;
            transform: translateY(0);
        }

    /* ── Highlights Cards ── */
.highlight-card {
            background: rgba(255, 255, 255, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.6);
            border-radius: var(--radius-card);
            padding: 2.25rem 1.75rem;
            box-shadow: var(--shadow-glass);
            transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            cursor: default;
        }
        .highlight-card:hover {
            transform: translateY(-6px) scale(1.01);
            box-shadow: 0 20px 48px rgba(60, 42, 31, 0.1);
            border-color: rgba(139, 111, 71, 0.15);
        }
        .highlight-card .icon {
            font-size: 2.2rem;
            margin-bottom: 1.25rem;
            display: inline-block;
            transition: transform 0.4s;
        }
        .highlight-card:hover .icon {
            transform: scale(1.1) rotate(-3deg);
        }
        .highlight-card h3 {
            font-family: 'Inter', sans-serif;
            font-size: 1.15rem;
            font-weight: 600;
            color: var(--dark-brown);
            margin-bottom: 0.5rem;
        }
        .highlight-card p {
            font-size: 0.9rem;
            color: #7A6B5D;
            line-height: 1.6;
        }

    /* ── Menu Preview ── */
.menu-item {
            border-radius: var(--radius-card);
            overflow: hidden;
            background: #fff;
            box-shadow: var(--shadow-glass);
            transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            cursor: pointer;
            position: relative;
        }
        .menu-item:hover {
            transform: translateY(-6px) scale(1.01);
            box-shadow: 0 20px 48px rgba(60, 42, 31, 0.1);
        }
        .menu-item .img-wrap {
            overflow: hidden;
            height: 200px;
        }
        .menu-item .img-wrap img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .menu-item:hover .img-wrap img {
            transform: scale(1.08);
        }
        .menu-item .overlay {
            position: absolute;
            inset: 0;
            background: rgba(60, 42, 31, 0.35);
            opacity: 0;
            transition: opacity 0.4s;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #fff;
            font-weight: 500;
            font-size: 0.9rem;
            letter-spacing: 1px;
            text-transform: uppercase;
        }
        .menu-item:hover .overlay {
            opacity: 1;
        }
        .menu-item .info {
            padding: 1.25rem 1.5rem 1.5rem;
        }
        .menu-item .info h4 {
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
            font-weight: 600;
            color: var(--dark-brown);
        }
        .menu-item .info .price {
            font-weight: 600;
            color: var(--warm-brown);
            font-size: 0.95rem;
        }
        .menu-item .info .desc {
            font-size: 0.85rem;
            color: #7A6B5D;
            margin-top: 0.25rem;
        }
        .menu-item .chef-badge {
            position: absolute;
            top: 12px;
            right: 12px;
            background: var(--muted-green);
            color: #fff;
            font-size: 0.65rem;
            font-weight: 600;
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            box-shadow: 0 4px 12px rgba(122, 158, 126, 0.3);
            z-index: 2;
            animation: pulseBadge 2.5s ease-in-out infinite;
        }
        @keyframes pulseBadge {
            0%,
            100% {
                box-shadow: 0 4px 12px rgba(122, 158, 126, 0.3);
            }
            50% {
                box-shadow: 0 4px 24px rgba(122, 158, 126, 0.5);
            }
        }

    /* ── Testimonials ── */
.testimonial-card {
            background: rgba(255, 255, 255, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.6);
            border-radius: var(--radius-card);
            padding: 2.5rem 2rem;
            box-shadow: var(--shadow-glass);
            text-align: center;
            max-width: 650px;
            margin: 0 auto;
            transition: opacity 0.6s ease, transform 0.6s ease;
        }
        .testimonial-card .stars {
            color: #E8C97A;
            font-size: 1.2rem;
            letter-spacing: 2px;
            margin-bottom: 1.25rem;
        }
        .testimonial-card blockquote {
            font-size: 1.1rem;
            line-height: 1.7;
            color: var(--dark-brown);
            font-weight: 300;
            font-style: italic;
        }
        .testimonial-card .author {
            margin-top: 1.5rem;
            font-weight: 600;
            font-size: 0.9rem;
            color: var(--warm-brown);
        }
        .testimonial-card .author span {
            font-weight: 400;
            color: #7A6B5D;
        }
        .testimonial-dots {
            display: flex;
            justify-content: center;
            gap: 0.6rem;
            margin-top: 2rem;
        }
        .testimonial-dots button {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            border: none;
            background: rgba(60, 42, 31, 0.15);
            cursor: pointer;
            transition: all 0.4s;
        }
        .testimonial-dots button.active {
            background: var(--warm-brown);
            width: 28px;
            border-radius: 5px;
        }
        .testimonial-dots button:hover {
            background: var(--warm-brown);
        }

/* ── Instagram Grid ── */
        .insta-item {
            border-radius: var(--radius-sm);
            overflow: hidden;
            aspect-ratio: 1;
            cursor: pointer;
            position: relative;
        }
        .insta-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.7s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .insta-item:hover img {
            transform: scale(1.08);
        }
        .insta-item .insta-overlay {
            position: absolute;
            inset: 0;
            background: rgba(60, 42, 31, 0.4);
            display: flex;
            align-items: center;
            justify-content: center;
            opacity: 0;
            transition: opacity 0.4s;
            color: #fff;
            font-size: 1.4rem;
        }
        .insta-item:hover .insta-overlay {
            opacity: 1;
        }

    /* ── CTA Section ── */
.cta-section {
            background: linear-gradient(135deg, var(--dark-brown) 0%, #4D3424 50%, var(--dark-brown) 100%);
            position: relative;
            overflow: hidden;
            padding: 5rem 2rem;
            text-align: center;
            color: #fff;
        }
        .cta-section::before {
            content: '';
            position: absolute;
            inset: 0;
            background:
                radial-gradient(ellipse at 30% 50%, rgba(139, 111, 71, 0.3) 0%, transparent 60%),
                radial-gradient(ellipse at 70% 50%, rgba(122, 158, 126, 0.15) 0%, transparent 50%);
            animation: gradientShift 8s ease-in-out infinite alternate;
        }
        @keyframes gradientShift {
            0% {
                transform: scale(1) rotate(0deg);
            }
            100% {
                transform: scale(1.05) rotate(2deg);
            }
        }
        .cta-section .content {
            position: relative;
            z-index: 2;
            max-width: 700px;
            margin: 0 auto;
        }
        .cta-section h2 {
            font-size: clamp(2.2rem, 5vw, 3.5rem);
            font-weight: 700;
            line-height: 1.1;
            margin-bottom: 1rem;
        }
        .cta-section p {
            font-size: 1.05rem;
            color: rgba(255, 248, 240, 0.75);
            margin-bottom: 2.5rem;
            font-weight: 300;
        }
        .cta-section .btn-group {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }
        .cta-section .btn-white {
            background: #fff;
            color: var(--dark-brown);
            border: none;
            padding: 0.9rem 2.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            box-shadow: 0 8px 28px rgba(0, 0, 0, 0.15);
        }
        .cta-section .btn-white:hover {
            transform: translateY(-3px) scale(1.02);
            box-shadow: 0 16px 40px rgba(0, 0, 0, 0.2);
        }
        .cta-section .btn-outline-light {
            background: transparent;
            color: #fff;
            border: 1.5px solid rgba(255, 248, 240, 0.35);
            padding: 0.9rem 2.5rem;
            border-radius: 50px;
            font-weight: 500;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .cta-section .btn-outline-light:hover {
            background: rgba(255, 248, 240, 0.1);
            border-color: rgba(255, 248, 240, 0.6);
            transform: translateY(-3px);
        }

    /* ── Menu Page Tabs ── */
.menu-tabs {
            display: flex;
            gap: 0.5rem;
            flex-wrap: wrap;
            margin-bottom: 3rem;
            border-bottom: 1px solid rgba(139, 111, 71, 0.12);
            padding-bottom: 1rem;
        }
        .menu-tabs button {
            background: none;
            border: none;
            padding: 0.5rem 1.25rem;
            font-family: 'Inter', sans-serif;
            font-size: 0.85rem;
            font-weight: 500;
            color: #7A6B5D;
            cursor: pointer;
            transition: all 0.35s;
            border-radius: 50px;
        }
        .menu-tabs button:hover {
            color: var(--dark-brown);
            background: rgba(139, 111, 71, 0.06);
        }
        .menu-tabs button.active {
            color: #fff;
            background: var(--dark-brown);
            box-shadow: 0 4px 14px rgba(60, 42, 31, 0.15);
        }
        .menu-grid .menu-item {
            transition: all 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94);
        }
        .menu-grid .menu-item.hidden-item {
            display: none;
        }

    /* ── About ── */
.about-story {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: center;
        }
        .about-story .image-wrap {
            border-radius: var(--radius-card);
            overflow: hidden;
            box-shadow: var(--shadow-soft);
        }
        .about-story .image-wrap img {
            width: 100%;
            height: 400px;
            object-fit: cover;
            transition: transform 0.7s;
        }
        .about-story .image-wrap:hover img {
            transform: scale(1.03);
        }
        @media (max-width: 768px) {
            .about-story {
                grid-template-columns: 1fr;
                gap: 2rem;
            }
            .about-story .image-wrap img {
                height: 280px;
            }
        }

.value-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            padding: 1.5rem;
            border-radius: var(--radius-card);
            background: rgba(255, 255, 255, 0.5);
            backdrop-filter: blur(8px);
            border: 1px solid rgba(255, 255, 255, 0.6);
            transition: all 0.4s;
        }
        .value-item:hover {
            transform: translateY(-4px);
            box-shadow: var(--shadow-glass);
        }
        .value-item .v-icon {
            font-size: 2.5rem;
            margin-bottom: 1rem;
            transition: transform 0.4s;
        }
        .value-item:hover .v-icon {
            transform: scale(1.1) rotate(-5deg);
        }
        .value-item h4 {
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
            font-weight: 600;
            color: var(--dark-brown);
        }
        .value-item p {
            font-size: 0.85rem;
            color: #7A6B5D;
            margin-top: 0.3rem;
        }

.team-member {
            text-align: center;
            transition: all 0.4s;
        }
        .team-member:hover {
            transform: translateY(-4px);
        }
        .team-member .avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            object-fit: cover;
            margin: 0 auto 1rem;
            box-shadow: 0 4px 20px rgba(60, 42, 31, 0.1);
            transition: transform 0.4s, box-shadow 0.4s;
            border: 3px solid rgba(255, 255, 255, 0.8);
        }
        .team-member:hover .avatar {
            transform: scale(1.05);
            box-shadow: 0 8px 32px rgba(60, 42, 31, 0.15);
        }
        .team-member h4 {
            font-family: 'Inter', sans-serif;
            font-size: 0.95rem;
            font-weight: 600;
            color: var(--dark-brown);
        }
        .team-member p {
            font-size: 0.8rem;
            color: #7A6B5D;
        }

    /* ── Gallery Masonry ── */
.masonry-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 1rem;
            grid-auto-flow: dense;
        }
        .masonry-grid .masonry-item {
            border-radius: var(--radius-sm);
            overflow: hidden;
            cursor: pointer;
            position: relative;
            transition: transform 0.4s;
        }
        .masonry-grid .masonry-item:hover {
            transform: scale(1.02);
        }
        .masonry-grid .masonry-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: block;
            transition: transform 0.6s;
        }
        .masonry-grid .masonry-item:hover img {
            transform: scale(1.06);
        }
        .masonry-grid .masonry-item.tall {
            grid-row: span 2;
        }
        .masonry-grid .masonry-item.wide {
            grid-column: span 2;
        }

    /* ── FAQ Accordion ── */
.faq-item {
            border-bottom: 1px solid rgba(139, 111, 71, 0.1);
            padding: 0.75rem 0;
        }
        .faq-item .faq-question {
            display: flex;
            justify-content: space-between;
            align-items: center;
            width: 100%;
            background: none;
            border: none;
            padding: 1rem 0;
            font-family: 'Inter', sans-serif;
            font-size: 1rem;
            font-weight: 500;
            color: var(--dark-brown);
            cursor: pointer;
            text-align: left;
            transition: color 0.3s;
        }
        .faq-item .faq-question:hover {
            color: var(--warm-brown);
        }
        .faq-item .faq-question .icon {
            font-size: 1.2rem;
            transition: transform 0.4s;
            color: var(--warm-brown);
        }
        .faq-item .faq-question .icon.open {
            transform: rotate(45deg);
        }
        .faq-item .faq-answer {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94), opacity 0.4s ease;
            opacity: 0;
        }
        .faq-item .faq-answer.open {
            max-height: 300px;
            opacity: 1;
        }
        .faq-item .faq-answer p {
            padding: 0 0 1.25rem;
            color: #7A6B5D;
            font-size: 0.92rem;
            line-height: 1.7;
        }

    /* ── Contact Form ── */
.contact-form input,
        .contact-form textarea,
        .contact-form select {
            width: 100%;
            padding: 0.9rem 1.25rem;
            border-radius: var(--radius-sm);
            border: 1.5px solid rgba(139, 111, 71, 0.12);
            background: rgba(255, 255, 255, 0.7);
            font-family: 'Inter', sans-serif;
            font-size: 0.9rem;
            color: var(--dark-brown);
            transition: all 0.35s;
            outline: none;
            backdrop-filter: blur(4px);
        }
        .contact-form input:focus,
        .contact-form textarea:focus {
            border-color: var(--warm-brown);
            box-shadow: 0 0 0 4px rgba(139, 111, 71, 0.08);
            background: #fff;
        }
        .contact-form textarea {
            resize: vertical;
            min-height: 130px;
        }
        .contact-form .input-group {
            position: relative;
        }
        .contact-form .input-group label {
            font-size: 0.8rem;
            font-weight: 500;
            color: var(--dark-brown);
            margin-bottom: 0.35rem;
            display: block;
        }
        .contact-form .submit-btn {
            background: var(--dark-brown);
            color: #fff;
            border: none;
            padding: 0.9rem 2.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
            transition: all 0.35s cubic-bezier(0.25, 0.46, 0.45, 0.94);
            box-shadow: 0 4px 14px rgba(60, 42, 31, 0.15);
            width: 100%;
        }
        .contact-form .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 28px rgba(60, 42, 31, 0.2);
            background: #4D3424;
        }
        .contact-form .success-msg {
            display: none;
            padding: 1.25rem;
            background: rgba(122, 158, 126, 0.1);
            border: 1px solid rgba(122, 158, 126, 0.2);
            border-radius: var(--radius-sm);
            color: var(--muted-green);
            font-weight: 500;
            text-align: center;
            animation: fadeIn 0.5s ease;
        }
        .contact-form .success-msg.show {
            display: block;
        }

    /* ── Map Placeholder ── */
.map-placeholder {
            border-radius: var(--radius-card);
            overflow: hidden;
            background: var(--beige);
            height: 280px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--warm-brown);
            font-weight: 400;
            font-size: 0.9rem;
            border: 1px solid rgba(139, 111, 71, 0.08);
        }
        .map-placeholder iframe {
            width: 100%;
            height: 100%;
            border: none;
            filter: grayscale(0.2) sepia(0.05);
        }

    /* ── Footer ── */
.footer {
            background: var(--dark-brown);
            color: rgba(255, 248, 240, 0.8);
            padding: 4rem 2rem 2rem;
        }
        .footer h4 {
            font-family: 'Inter', sans-serif;
            font-size: 0.85rem;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            color: var(--light-gold);
            margin-bottom: 1rem;
        }
        .footer a {
            color: rgba(255, 248, 240, 0.65);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.3s;
            display: inline-block;
        }
        .footer a:hover {
            color: var(--light-gold);
        }
        .footer .newsletter input {
            background: rgba(255, 255, 255, 0.08);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 0.7rem 1rem;
            border-radius: 50px;
            color: #fff;
            font-size: 0.85rem;
            width: 100%;
            outline: none;
            transition: all 0.3s;
        }
        .footer .newsletter input::placeholder {
            color: rgba(255, 248, 240, 0.35);
        }
        .footer .newsletter input:focus {
            border-color: var(--light-gold);
            background: rgba(255, 255, 255, 0.12);
        }
        .footer .newsletter button {
            background: var(--light-gold);
            color: var(--dark-brown);
            border: none;
            padding: 0.7rem 1.5rem;
            border-radius: 50px;
            font-weight: 600;
            font-size: 0.85rem;
            cursor: pointer;
            transition: all 0.3s;
            white-space: nowrap;
        }
        .footer .newsletter button:hover {
            background: #fff;
            transform: translateY(-2px);
        }
        .footer .social a {
            font-size: 1.2rem;
            padding: 0.4rem;
            transition: transform 0.3s, color 0.3s;
            display: inline-block;
        }
        .footer .social a:hover {
            transform: translateY(-3px) scale(1.1);
        }
        .footer .copyright {
            border-top: 1px solid rgba(255, 248, 240, 0.06);
            padding-top: 1.5rem;
            margin-top: 2rem;
            font-size: 0.8rem;
            color: rgba(255, 248, 240, 0.35);
        }

    /* ── Lightbox ── */
.lightbox {
            position: fixed;
            inset: 0;
            z-index: 9998;
            background: rgba(0, 0, 0, 0.85);
            backdrop-filter: blur(12px);
            display: none;
            align-items: center;
            justify-content: center;
            padding: 2rem;
            cursor: pointer;
            animation: fadeIn 0.3s ease;
        }
        .lightbox.open {
            display: flex;
        }
        .lightbox img {
            max-width: 90vw;
            max-height: 85vh;
            border-radius: var(--radius-sm);
            box-shadow: 0 40px 80px rgba(0, 0, 0, 0.4);
            object-fit: contain;
        }
        .lightbox .close {
            position: absolute;
            top: 1.5rem;
            right: 2rem;
            color: #fff;
            font-size: 2rem;
            cursor: pointer;
            opacity: 0.6;
            transition: opacity 0.3s;
            background: none;
            border: none;
        }
        .lightbox .close:hover {
            opacity: 1;
        }

    /* ── Responsive Tweaks ── */
@media (max-width: 640px) {
            .section {
                padding: 4rem 1.25rem;
            }
            .hero {
                padding: 6rem 1.25rem 4rem;
                min-height: 85vh;
            }
            .hero-content h1 {
                font-size: clamp(2.4rem, 10vw, 3.5rem);
            }
            .hero-buttons .btn-primary,
            .hero-buttons .btn-secondary {
                padding: 0.75rem 1.75rem;
                font-size: 0.85rem;
                width: 100%;
            }
            .cta-section .btn-white,
            .cta-section .btn-outline-light {
                width: 100%;
            }
            .masonry-grid {
                grid-template-columns: 1fr 1fr;
            }
            .masonry-grid .masonry-item.tall,
            .masonry-grid .masonry-item.wide {
                grid-row: auto;
                grid-column: auto;
            }
            .footer .newsletter form {
                flex-direction: column;
            }
            .footer .newsletter button {
                width: 100%;
            }
        }

@media (min-width: 641px) and (max-width: 1024px) {
            .section {
                padding: 5rem 2rem;
            }
            .about-story {
                gap: 2.5rem;
            }
        }

    /* ── Grain Texture Overlay ── */
.grain-overlay {
            pointer-events: none;
            position: fixed;
            inset: 0;
            z-index: 9997;
            opacity: 0.025;
            background-image: url('data:image/svg+xml,%3Csvg viewBox="0 0 200 200" xmlns="http://www.w3.org/2000/svg"%3E%3Cfilter id="n"%3E%3CfeTurbulence type="fractalNoise" baseFrequency="0.75" numOctaves="4" stitchTiles="stitch"/%3E%3C/filter%3E%3Crect width="100%25" height="100%25" filter="url(%23n)"/%3E%3C/svg%3E');
            background-size: 200px 200px;
        }

    /* ── Loading spinner for form ── */
.spinner {
            display: inline-block;
            width: 18px;
            height: 18px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            border-top-color: #fff;
            border-radius: 50%;
            animation: spin 0.7s linear infinite;
            vertical-align: middle;
            margin-right: 6px;
        }
        @keyframes spin {
            to {
                transform: rotate(360deg);
            }
        }

    /* ── Smooth section separators ── */
.section-divider {
            height: 1px;
            background: linear-gradient(to right, transparent, rgba(139, 111, 71, 0.08), transparent);
            max-width: 1200px;
            margin: 0 auto;
        }

    /* ── Focus visible for accessibility ── */
*:focus-visible {
            outline: 2px solid var(--warm-brown);
            outline-offset: 2px;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <-- Scroll Progress -->
    <div id="scroll-progress" role="progressbar" aria-label="Page scroll progress"></div>
    <-- Grain Overlay -->
    <div class="grain-overlay" aria-hidden="true"></div>
<!-- Lightbox -->
    <div class="lightbox" id="lightbox" role="dialog" aria-modal="true" aria-label="Image lightbox">
        <button class="close" id="lightbox-close" aria-label="Close lightbox">&times;</button>
        <img id="lightbox-img" src="" alt="Enlarged view" />
    </div>
<!-- ──── NAVBAR ──── -->
    <header class="navbar" id="navbar" role="banner">
        <div class="flex items-center justify-between max-w-7xl mx-auto">
            <a href="#home" class="logo" aria-label="Brew & Co. home">Brew & Co.</a>

<nav class="nav-links flex items-center gap-6" id="nav-links" aria-label="Main navigation">
                <a href="#home" class="nav-link" data-nav>Home</a>
                <a href="#menu" class="nav-link" data-nav>Menu</a>
                <a href="#about" class="nav-link" data-nav>About</a>
                <a href="#faq" class="nav-link" data-nav>FAQ</a>
                <a href="#contact" class="nav-link" data-nav>Contact</a>
                <button class="cta-btn-mobile" onclick="document.querySelector('[data-nav-cta]').click()">Order Online</button>
            </nav>

<button class="cta-btn hidden md:inline-block" data-nav-cta onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Order Online</button>

<button class="mobile-toggle" id="mobile-toggle" aria-label="Toggle navigation menu" aria-expanded="false">
                <span></span><span></span><span></span>
            </button>
        </div>
    </header>

<!-- ──── HERO ──── -->
<section id="home" class="hero" aria-label="Hero">
        <div class="hero-bg" aria-hidden="true"></div>
        <div class="hero-bg-image" id="hero-parallax" aria-hidden="true"></div>

<div class="hero-content">
            <span class="badge">☕ Specialty Coffee Since 2018</span>
            <h1>Where Every Cup <br /><span class="highlight">Tells a Story</span></h1>
            <p>Handcrafted coffee &amp; artisan food in a space built for connection. Welcome to your new favorite place.</p>
            <div class="hero-buttons">
                <button class="btn-primary" onclick="document.getElementById('menu').scrollIntoView({behavior:'smooth'})">View Menu</button>
                <button class="btn-secondary" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Visit Us</button>
            </div>
        </div>

<div class="hero-scroll-indicator" aria-hidden="true">
            <span>Scroll</span>
            <div class="scroll-line"></div>
        </div>
    </section>

<!-- ──── HIGHLIGHTS ──── -->
<section class="section" aria-label="Highlights">
        <div class="text-center mb-12 reveal">
            <span class="section-label">Why We're Different</span>
            <h2 class="section-title">Crafted with Purpose</h2>
            <p class="section-subtitle mx-auto">Every detail, from bean to cup, is designed to create moments of warmth and connection.</p>
        </div>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
            <div class="highlight-card stagger-item">
                <div class="icon">🌱</div>
                <h3>Freshly Roasted</h3>
                <p>Single-origin beans roasted in-house every week for peak flavor.</p>
            </div>
            <div class="highlight-card stagger-item">
                <div class="icon">🥐</div>
                <h3>Artisan Pastries</h3>
                <p>Baked daily using local, seasonal ingredients. Flaky, buttery, unforgettable.</p>
            </div>
            <div class="highlight-card stagger-item">
                <div class="icon">📶</div>
                <h3>Free WiFi</h3>
                <p>Fast, reliable WiFi for working, studying, or catching up with friends.</p>
            </div>
            <div class="highlight-card stagger-item">
                <div class="icon">🎭</div>
                <h3>Community Events</h3>
                <p>Open mic nights, art showcases, and coffee workshops every month.</p>
            </div>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── SIGNATURE MENU PREVIEW ──── -->
 <section class="section" aria-label="Signature Menu Preview">
        <div class="text-center mb-12 reveal">
            <span class="section-label">Our Signatures</span>
            <h2 class="section-title">From Our Kitchen to Your Heart</h2>
            <p class="section-subtitle mx-auto">A curated selection of our most-loved drinks and dishes.</p>
        </div>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
            <div class="menu-item stagger-item">
                <div class="img-wrap">
                    <img src="https://images.unsplash.com/photo-1572442388796-11668a67e53d?q=80&w=1974&auto=format&fit=crop" alt="Honey Lavender Latte" loading="lazy" />
                </div>
                <div class="overlay">Try It</div>
                <div class="info">
                    <div class="flex justify-between items-start">
                        <h4>Honey Lavender Latte</h4>
                        <span class="price">$5.50</span>
                    </div>
                    <p class="desc">Espresso, steamed oat milk, local honey &amp; lavender</p>
                </div>
            </div>
            <div class="menu-item stagger-item">
                <div class="img-wrap">
                    <img src="https://images.unsplash.com/photo-1509365465985-25d11c17e812?q=80&w=1974&auto=format&fit=crop" alt="Smoked Salmon Toast" loading="lazy" />
                </div>
                <div class="overlay">Try It</div>
                <div class="info">
                    <div class="flex justify-between items-start">
                        <h4>Smoked Salmon Toast</h4>
                        <span class="price">$12.00</span>
                    </div>
                    <p class="desc">Sourdough, smoked salmon, dill cream cheese, capers</p>
                </div>
            </div>
            <div class="menu-item stagger-item">
                <div class="img-wrap">
                    <img src="https://images.unsplash.com/photo-1558857563-b371033873b8?q=80&w=1974&auto=format&fit=crop" alt="Macha Tiramisu" loading="lazy" />
                </div>
                <div class="chef-badge">Chef's Special</div>
                <div class="overlay">Try It</div>
                <div class="info">
                    <div class="flex justify-between items-start">
                        <h4>Macha Tiramisu</h4>
                        <span class="price">$8.50</span>
                    </div>
                    <p class="desc">Layers of matcha sponge, mascarpone &amp; white chocolate</p>
                </div>
            </div>
            <div class="menu-item stagger-item">
                <div class="img-wrap">
                    <img src="https://images.unsplash.com/photo-1461023058943-07fcbe16d735?q=80&w=2070&auto=format&fit=crop" alt="Cold Brew Tonic" loading="lazy" />
                </div>
                <div class="overlay">Try It</div>
                <div class="info">
                    <div class="flex justify-between items-start">
                        <h4>Cold Brew Tonic</h4>
                        <span class="price">$4.75</span>
                    </div>
                    <p class="desc">Cold brew concentrate, tonic water, orange twist</p>
                </div>
            </div>
        </div>
        <div class="text-center mt-10 reveal">
            <button class="hero-buttons .btn-primary inline-block bg-[var(--dark-brown)] text-[var(--cream)] px-8 py-3 rounded-full font-semibold text-sm shadow-lg hover:shadow-xl transition-all hover:-translate-y-1" onclick="document.getElementById('menu').scrollIntoView({behavior:'smooth'})">View Full Menu &rarr;</button>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── TESTIMONIALS ──── -->
<section class="section" aria-label="Testimonials">
        <div class="text-center mb-12 reveal">
            <span class="section-label">Testimonials</span>
            <h2 class="section-title">What Our Community Says</h2>
        </div>
        <div class="relative">
            <div class="testimonial-card" id="testimonial-card">
                <div class="stars" id="testimonial-stars">★★★★★</div>
                <blockquote id="testimonial-text">"The most incredible coffee experience. Every drink is crafted with such care and intention. It's my happy place."</blockquote>
                <div class="author" id="testimonial-author">— Sarah M. <span>Regular</span></div>
            </div>
            <div class="testimonial-dots" id="testimonial-dots" role="tablist" aria-label="Testimonial navigation"></div>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── INSTAGRAM FEED ──── -->
<section class="section" aria-label="Instagram Feed">
        <div class="text-center mb-10 reveal">
            <span class="section-label">@brewandco</span>
            <h2 class="section-title">Follow Us on Instagram</h2>
            <p class="section-subtitle mx-auto">Tag us in your photos for a chance to be featured.</p>
        </div>
        <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-6 gap-2 reveal">
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=2070&auto=format&fit=crop" alt="Coffee art" loading="lazy" /><div class="insta-overlay">📷</div></div>
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1600093463592-8e36ae410545?q=80&w=2070&auto=format&fit=crop" alt="Pastry" loading="lazy" /><div class="insta-overlay">📷</div></div>
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?q=80&w=2078&auto=format&fit=crop" alt="Cafe interior" loading="lazy" /><div class="insta-overlay">📷</div></div>
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1442512595331-e89e73853f31?q=80&w=2070&auto=format&fit=crop" alt="Coffee beans" loading="lazy" /><div class="insta-overlay">📷</div></div>
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1498804103079-a6351b050096?q=80&w=2070&auto=format&fit=crop" alt="Latte art" loading="lazy" /><div class="insta-overlay">📷</div></div>
            <div class="insta-item"><img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?q=80&w=1974&auto=format&fit=crop" alt="Cafe vibes" loading="lazy" /><div class="insta-overlay">📷</div></div>
        </div>
    </section>

<!-- ──── CTA SECTION ──── -->
<section class="cta-section" aria-label="Call to action">
        <div class="content reveal">
            <h2>Ready for Your Next <br />Favorite Cup?</h2>
            <p>Come in, settle in, and let us take care of the rest. Your table is waiting.</p>
            <div class="btn-group">
                <button class="btn-white" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Book a Table</button>
                <button class="btn-outline-light" onclick="document.getElementById('menu').scrollIntoView({behavior:'smooth'})">Order Online</button>
            </div>
        </div>
    </section>

<!-- ──── MENU PAGE ──── -->
<section id="menu" class="section" aria-label="Full Menu">
        <div class="text-center mb-10 reveal">
            <span class="section-label">Our Menu</span>
            <h2 class="section-title">Crafted for Every Craving</h2>
            <p class="section-subtitle mx-auto">From bold espresso to delicate pastries — explore our full offering.</p>
        </div>

<div class="menu-tabs reveal" role="tablist" aria-label="Menu categories">
            <button class="active" data-tab="coffee" role="tab" aria-selected="true">☕ Coffee</button>
            <button data-tab="tea" role="tab" aria-selected="false">🍵 Tea</button>
            <button data-tab="breakfast" role="tab" aria-selected="false">🍳 Breakfast</button>
            <button data-tab="desserts" role="tab" aria-selected="false">🍰 Desserts</button>
            <button data-tab="specials" role="tab" aria-selected="false">✨ Specials</button>
        </div>

<div class="menu-grid grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-5" id="menu-grid">
            <!-- Coffee -->
            <div class="menu-item" data-category="coffee">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1572442388796-11668a67e53d?q=80&w=1974&auto=format&fit=crop" alt="Honey Lavender Latte" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Honey Lavender Latte</h4><span class="price">$5.50</span></div><p class="desc">Oat milk, local honey &amp; lavender</p></div>
            </div>
            <div class="menu-item" data-category="coffee">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1461023058943-07fcbe16d735?q=80&w=2070&auto=format&fit=crop" alt="Cold Brew Tonic" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Cold Brew Tonic</h4><span class="price">$4.75</span></div><p class="desc">Tonic water, orange twist, ice</p></div>
            </div>
            <div class="menu-item" data-category="coffee">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?q=80&w=1974&auto=format&fit=crop" alt="Classic Espresso" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Classic Espresso</h4><span class="price">$3.25</span></div><p class="desc">Double shot, single origin</p></div>
            </div>
            <div class="menu-item" data-category="coffee">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1570968915860-54d5c301fa9f?q=80&w=1974&auto=format&fit=crop" alt="Cappuccino" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Cappuccino</h4><span class="price">$4.50</span></div><p class="desc">Velvety foam, chocolate dust</p></div>
            </div>
            <!-- Tea -->
            <div class="menu-item" data-category="tea">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1556679343-c7306c1976bc?q=80&w=1964&auto=format&fit=crop" alt="Matcha Latte" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Matcha Latte</h4><span class="price">$5.25</span></div><p class="desc">Ceremonial matcha, oat milk</p></div>
            </div>
            <div class="menu-item" data-category="tea">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1571934811356-5cc061b6821f?q=80&w=1974&auto=format&fit=crop" alt="Chai Latte" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Chai Latte</h4><span class="price">$4.95</span></div><p class="desc">House-spiced, honey, steamed milk</p></div>
            </div>
            <div class="menu-item" data-category="tea">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1594631252845-29fc4cc8cde9?q=80&w=1974&auto=format&fit=crop" alt="Herbal Infusion" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Herbal Infusion</h4><span class="price">$3.75</span></div><p class="desc">Chamomile, lavender, honey</p></div>
            </div>
            <!-- Breakfast -->
            <div class="menu-item" data-category="breakfast">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1509365465985-25d11c17e812?q=80&w=1974&auto=format&fit=crop" alt="Smoked Salmon Toast" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Smoked Salmon Toast</h4><span class="price">$12.00</span></div><p class="desc">Dill cream cheese, capers, lemon</p></div>
            </div>
            <div class="menu-item" data-category="breakfast">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1525351484163-7529414344d8?q=80&w=2080&auto=format&fit=crop" alt="Avocado Toast" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Avocado Toast</h4><span class="price">$10.50</span></div><p class="desc">Sourdough, chili flakes, lime</p></div>
            </div>
            <div class="menu-item" data-category="breakfast">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1533089860892-a7c6f0a88666?q=80&w=2070&auto=format&fit=crop" alt="Granola Bowl" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Granola Bowl</h4><span class="price">$9.00</span></div><p class="desc">Yogurt, berries, house granola</p></div>
            </div>
            <!-- Desserts -->
            <div class="menu-item" data-category="desserts">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1558857563-b371033873b8?q=80&w=1974&auto=format&fit=crop" alt="Matcha Tiramisu" loading="lazy" /></div>
                <div class="chef-badge">Chef's Special</div>
                <div class="info"><div class="flex justify-between"><h4>Matcha Tiramisu</h4><span class="price">$8.50</span></div><p class="desc">Mascarpone, white chocolate</p></div>
            </div>
            <div class="menu-item" data-category="desserts">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1488477181946-6428a0291777?q=80&w=1974&auto=format&fit=crop" alt="Flourless Chocolate Cake" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Flourless Chocolate Cake</h4><span class="price">$7.50</span></div><p class="desc">Rich, gluten-free, raspberry coulis</p></div>
            </div>
            <div class="menu-item" data-category="desserts">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1551024506-0bccd828d307?q=80&w=1964&auto=format&fit=crop" alt="Vegan Cookie Trio" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Vegan Cookie Trio</h4><span class="price">$5.00</span></div><p class="desc">Chocolate, oat, coconut</p></div>
            </div>
            <!-- Specials -->
            <div class="menu-item" data-category="specials">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1514432324607-a09d9b4aefda?q=80&w=1974&auto=format&fit=crop" alt="Seasonal Pumpkin Spice Latte" loading="lazy" /></div>
                <div class="chef-badge">Limited</div>
                <div class="info"><div class="flex justify-between"><h4>PSL</h4><span class="price">$5.75</span></div><p class="desc">Pumpkin, cinnamon, whipped cream</p></div>
            </div>
            <div class="menu-item" data-category="specials">
                <div class="img-wrap"><img src="https://images.unsplash.com/photo-1567620905732-2d1ec7ab7445?q=80&w=1980&auto=format&fit=crop" alt="Truffle Mushroom Croissant" loading="lazy" /></div>
                <div class="info"><div class="flex justify-between"><h4>Truffle Mushroom Croissant</h4><span class="price">$11.00</span></div><p class="desc">Gruyère, thyme, arugula</p></div>
            </div>
        </div>

<div class="text-center mt-8 reveal">
            <button class="bg-[var(--beige)] text-[var(--dark-brown)] px-6 py-2.5 rounded-full font-medium text-sm border border-[rgba(139,111,71,0.15)] hover:bg-[var(--warm-brown)] hover:text-white transition-all">📄 Download PDF Menu</button>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── ABOUT PAGE ──── -->
<section id="about" class="section" aria-label="About Us">
        <div class="text-center mb-14 reveal">
            <span class="section-label">Our Story</span>
            <h2 class="section-title">Born from a Love for <br />Connection &amp; Craft</h2>
        </div>

<div class="about-story mb-16 reveal">
            <div class="image-wrap">
                <img src="https://images.unsplash.com/photo-1442512595331-e89e73853f31?q=80&w=2070&auto=format&fit=crop" alt="Our café interior" loading="lazy" />
            </div>
            <div>
                <p class="text-lg font-serif italic text-[var(--warm-brown)] mb-4">"We believe coffee is more than a drink — it's a reason to pause, connect, and feel at home."</p>
                <p class="text-[#7A6B5D] leading-relaxed mb-4">Brew &amp; Co. opened its doors in 2018 with a simple mission: create a space where every person feels welcome and every cup is made with intention. We source our beans directly from small farms, roast in small batches, and craft every drink by hand.</p>
                <p class="text-[#7A6B5D] leading-relaxed">Our café is a gathering place for writers, thinkers, friends, and families. We host monthly art shows, open mic nights, and coffee workshops because we believe community is the richest ingredient.</p>
            </div>
        </div>

<!-- Mission & Values -->
<div class="text-center mb-10 reveal">
            <span class="section-label">Our Values</span>
            <h2 class="section-title text-3xl">What We Stand For</h2>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-16">
            <div class="value-item stagger-item"><div class="v-icon">🤝</div><h4>Community First</h4><p>Every event, every seat — built for connection.</p></div>
            <div class="value-item stagger-item"><div class="v-icon">🌍</div><h4>Sustainable Sourcing</h4><p>Direct trade, compostable cups, zero waste.</p></div>
            <div class="value-item stagger-item"><div class="v-icon">❤️</div><h4>Crafted with Love</h4><p>From bean to plate, everything is handmade.</p></div>
            <div class="value-item stagger-item"><div class="v-icon">✨</div><h4>Inclusivity</h4><p>Every identity, every story — you belong here.</p></div>
        </div>

<!-- Meet the Team -->
<div class="text-center mb-10 reveal">
            <span class="section-label">Meet the Team</span>
            <h2 class="section-title text-3xl">The Faces Behind Your Cup</h2>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-16">
            <div class="team-member stagger-item">
                <img class="avatar" src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?q=80&w=1974&auto=format&fit=crop" alt="Leo" loading="lazy" />
                <h4>Leo Torres</h4>
                <p>Head Barista</p>
                <div class="flex justify-center gap-2 mt-2 text-[var(--warm-brown)]">
                    <a href="#" aria-label="Instagram">📸</a>
                    <a href="#" aria-label="LinkedIn">💼</a>
                </div>
            </div>
            <div class="team-member stagger-item">
                <img class="avatar" src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?q=80&w=1974&auto=format&fit=crop" alt="Maya" loading="lazy" />
                <h4>Maya Chen</h4>
                <p>Pastry Chef</p>
                <div class="flex justify-center gap-2 mt-2 text-[var(--warm-brown)]">
                    <a href="#" aria-label="Instagram">📸</a>
                    <a href="#" aria-label="LinkedIn">💼</a>
                </div>
            </div>
            <div class="team-member stagger-item">
                <img class="avatar" src="https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?q=80&w=1974&auto=format&fit=crop" alt="James" loading="lazy" />
                <h4>James Okonkwo</h4>
                <p>Roaster</p>
                <div class="flex justify-center gap-2 mt-2 text-[var(--warm-brown)]">
                    <a href="#" aria-label="Instagram">📸</a>
                    <a href="#" aria-label="LinkedIn">💼</a>
                </div>
            </div>
            <div class="team-member stagger-item">
                <img class="avatar" src="https://images.unsplash.com/photo-1438761681033-6461ffad8d80?q=80&w=2070&auto=format&fit=crop" alt="Priya" loading="lazy" />
                <h4>Priya Sharma</h4>
                <p>Events &amp; Community</p>
                <div class="flex justify-center gap-2 mt-2 text-[var(--warm-brown)]">
                    <a href="#" aria-label="Instagram">📸</a>
                    <a href="#" aria-label="LinkedIn">💼</a>
                </div>
            </div>
        </div>

<!-- Behind the Scenes Gallery -->
<div class="text-center mb-10 reveal">
            <span class="section-label">Behind the Scenes</span>
            <h2 class="section-title text-3xl">Moments That Make Us</h2>
        </div>
        <div class="masonry-grid reveal">
            <div class="masonry-item"><img src="https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?q=80&w=2070&auto=format&fit=crop" alt="Pour over coffee" loading="lazy" onclick="openLightbox(this.src)" /></div>
            <div class="masonry-item tall"><img src="https://images.unsplash.com/photo-1501339847302-ac426a4a7cbb?q=80&w=2078&auto=format&fit=crop" alt="Cafe interior" loading="lazy" onclick="openLightbox(this.src)" /></div>
            <div class="masonry-item"><img src="https://images.unsplash.com/photo-1600093463592-8e36ae410545?q=80&w=2070&auto=format&fit=crop" alt="Pastry display" loading="lazy" onclick="openLightbox(this.src)" /></div>
            <div class="masonry-item wide"><img src="https://images.unsplash.com/photo-1442512595331-e89e73853f31?q=80&w=2070&auto=format&fit=crop" alt="Coffee beans" loading="lazy" onclick="openLightbox(this.src)" /></div>
            <div class="masonry-item"><img src="https://images.unsplash.com/photo-1498804103079-a6351b050096?q=80&w=2070&auto=format&fit=crop" alt="Latte art" loading="lazy" onclick="openLightbox(this.src)" /></div>
            <div class="masonry-item"><img src="https://images.unsplash.com/photo-1509042239860-f550ce710b93?q=80&w=1974&auto=format&fit=crop" alt="Coffee cup" loading="lazy" onclick="openLightbox(this.src)" /></div>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── FAQ PAGE ──── -->
<section id="faq" class="section" aria-label="Frequently Asked Questions">
        <div class="text-center mb-12 reveal">
            <span class="section-label">FAQ</span>
            <h2 class="section-title">Your Questions, Answered</h2>
            <p class="section-subtitle mx-auto">Everything you need to know before your visit.</p>
        </div>
        <div class="max-w-3xl mx-auto reveal" id="faq-container">
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">Do you offer vegan options? <span class="icon">+</span></button>
                <div class="faq-answer"><p>Yes! We have a variety of vegan drinks (oat, almond, soy) and food items — from our Vegan Cookie Trio to the Avocado Toast. Just ask our team for recommendations!</p></div>
            </div>
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">Do you have free WiFi? <span class="icon">+</span></button>
                <div class="faq-answer"><p>Absolutely. Our WiFi is free, fast, and open to all customers. The password is printed on your receipt.</p></div>
            </div>
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">Can I book private events? <span class="icon">+</span></button>
                <div class="faq-answer"><p>Yes! We host private gatherings, birthday parties, and corporate meetings. Our back room seats up to 30 guests. Email us at events@brewandco.com to book.</p></div>
            </div>
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">Where do you source your coffee? <span class="icon">+</span></button>
                <div class="faq-answer"><p>We source single-origin beans directly from farms in Ethiopia, Colombia, and Guatemala. Every batch is roasted in-house within 48 hours of your cup.</p></div>
            </div>
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">What are your opening hours? <span class="icon">+</span></button>
                <div class="faq-answer"><p>We're open Monday–Friday 7am–7pm, Saturday 8am–8pm, and Sunday 8am–5pm. Holiday hours may vary — check our Instagram for updates.</p></div>
            </div>
            <div class="faq-item">
                <button class="faq-question" aria-expanded="false">Do you have gluten-free options? <span class="icon">+</span></button>
                <div class="faq-answer"><p>Yes! Many of our menu items are gluten-free or can be modified. Our Flourless Chocolate Cake is a favorite, and we offer gluten-free bread for toasts.</p></div>
            </div>
        </div>
    </section>

<div class="section-divider"></div>

<!-- ──── CONTACT PAGE ──── -->
<section id="contact" class="section" aria-label="Contact Us">
        <div class="text-center mb-12 reveal">
            <span class="section-label">Get in Touch</span>
            <h2 class="section-title">We'd Love to Hear From You</h2>
            <p class="section-subtitle mx-auto">Reserve a table, ask a question, or just say hello.</p>
        </div>

<div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
            <div class="reveal-left">
                <form class="contact-form space-y-5" id="contact-form" novalidate>
                    <div class="input-group">
                        <label for="form-name">Full Name</label>
                        <input type="text" id="form-name" name="name" placeholder="Your name" required autocomplete="name" />
                    </div>
                    <div class="input-group">
                        <label for="form-email">Email Address</label>
                        <input type="email" id="form-email" name="email" placeholder="you@example.com" required autocomplete="email" />
                    </div>
                    <div class="input-group">
                        <label for="form-phone">Phone (optional)</label>
                        <input type="tel" id="form-phone" name="phone" placeholder="+1 555 000 0000" autocomplete="tel" />
                    </div>
                    <div class="input-group">
                        <label for="form-message">Message</label>
                        <textarea id="form-message" name="message" placeholder="Tell us how we can help..." required></textarea>
                    </div>
                    <button type="submit" class="submit-btn" id="form-submit">Send Message</button>
                    <div class="success-msg" id="form-success">✓ Thanks for reaching out! We'll get back to you within 24 hours.</div>
                </form>
            </div>

<div class="reveal-right space-y-6">
                <div class="map-placeholder">
                    <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3151.8354345093667!2d144.9537353153167!3d-37.81627997975159!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x6ad65d5df1f5a2b7%3A0x5045675218ce6e0!2sMelbourne%20VIC%2C%20Australia!5e0!3m2!1sen!2sus!4v1680000000000" loading="lazy" referrerpolicy="no-referrer-when-downgrade" title="Map showing Brew & Co. location"></iframe>
                </div>

<div class="bg-white/60 backdrop-blur-sm rounded-[var(--radius-card)] p-6 border border-white/60 shadow-[var(--shadow-glass)]">
                    <h4 class="font-sans font-semibold text-[var(--dark-brown)] mb-3">📍 Visit Us</h4>
                    <p class="text-[#7A6B5D] text-sm leading-relaxed">42 Anderson Street, Melbourne VIC 3000</p>
                    <hr class="my-3 border-[rgba(139,111,71,0.08)]" />
                    <div class="flex flex-col gap-1 text-sm">
                        <span class="text-[#7A6B5D]"><strong class="text-[var(--dark-brown)]">Hours:</strong> Mon–Fri 7am–7pm · Sat 8am–8pm · Sun 8am–5pm</span>
                        <span class="text-[#7A6B5D]"><strong class="text-[var(--dark-brown)]">Phone:</strong> <a href="tel:+15551234567" class="hover:text-[var(--warm-brown)] transition-colors">(555) 123-4567</a></span>
                        <span class="text-[#7A6B5D]"><strong class="text-[var(--dark-brown)]">Email:</strong> <a href="mailto:hello@brewandco.com" class="hover:text-[var(--warm-brown)] transition-colors">hello@brewandco.com</a></span>
                    </div>
                </div>

<div class="flex gap-4 text-2xl justify-center lg:justify-start">
                    <a href="#" aria-label="Instagram" class="text-[var(--warm-brown)] hover:text-[var(--dark-brown)] transition-all hover:-translate-y-1">📸</a>
                    <a href="#" aria-label="Facebook" class="text-[var(--warm-brown)] hover:text-[var(--dark-brown)] transition-all hover:-translate-y-1">👍</a>
                    <a href="#" aria-label="Twitter" class="text-[var(--warm-brown)] hover:text-[var(--dark-brown)] transition-all hover:-translate-y-1">🐦</a>
                    <a href="#" aria-label="TikTok" class="text-[var(--warm-brown)] hover:text-[var(--dark-brown)] transition-all hover:-translate-y-1">🎵</a>
                </div>
            </div>
        </div>
    </section>

<!-- ──── FOOTER ──── -->
<footer class="footer" role="contentinfo">
        <div class="max-w-7xl mx-auto">
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 mb-8">
                <div>
                    <h4>Brew &amp; Co.</h4>
                    <p class="text-sm text-[rgba(255,248,240,0.5)] leading-relaxed max-w-xs">Where every cup tells a story. Specialty coffee &amp; handcrafted food in the heart of the community.</p>
                </div>
                <div>
                    <h4>Quick Links</h4>
                    <div class="flex flex-col gap-2">
                        <a href="#home">Home</a>
                        <a href="#menu">Menu</a>
                        <a href="#about">About</a>
                        <a href="#faq">FAQ</a>
                        <a href="#contact">Contact</a>
                    </div>
                </div>
                <div>
                    <h4>Connect</h4>
                    <div class="social flex gap-2">
                        <a href="#" aria-label="Instagram">📸</a>
                        <a href="#" aria-label="Facebook">👍</a>
                        <a href="#" aria-label="Twitter">🐦</a>
                        <a href="#" aria-label="TikTok">🎵</a>
                    </div>
                    <div class="mt-3 text-sm text-[rgba(255,248,240,0.5)]">
                        <p>42 Anderson Street<br />Melbourne VIC 3000</p>
                    </div>
                </div>
                <div>
                    <h4>Newsletter</h4>
                    <p class="text-sm text-[rgba(255,248,240,0.5)] mb-3">Get 10% off your first order + weekly updates.</p>
                    <div class="newsletter">
                        <form id="newsletter-form" class="flex gap-2">
                            <input type="email" placeholder="Your email" required aria-label="Email for newsletter" />
                            <button type="submit">Join</button>
                        </form>
                        <p class="text-xs text-[rgba(255,248,240,0.3)] mt-2" id="newsletter-msg"></p>
                    </div>
                </div>
            </div>
            <div class="copyright text-center lg:text-left">
                &copy; 2026 Brew &amp; Co. All rights reserved. Crafted with ☕ &amp; ❤️.
            </div>
        </div>
    </footer>

<!-- ──── JAVASCRIPT ──── -->
<script>
        (function() {
            'use strict';

// ── Scroll Progress ──
            const progressBar = document.getElementById('scroll-progress');
            window.addEventListener('scroll', function() {
                const scrollTop = window.scrollY;
                const docHeight = document.documentElement.scrollHeight - window.innerHeight;
                const progress = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
                progressBar.style.width = progress + '%';
            });

// ── Navbar scroll effect ──
            const navbar = document.getElementById('navbar');
            window.addEventListener('scroll', function() {
                if (window.scrollY > 60) {
                    navbar.classList.add('scrolled');
                } else {
                    navbar.classList.remove('scrolled');
                }
            });

// ── Mobile toggle ──
            const toggleBtn = document.getElementById('mobile-toggle');
            const navLinks = document.getElementById('nav-links');
            toggleBtn.addEventListener('click', function() {
                const isOpen = navLinks.classList.toggle('open');
                toggleBtn.classList.toggle('active');
                toggleBtn.setAttribute('aria-expanded', isOpen);
            });
            document.querySelectorAll('[data-nav]').forEach(function(link) {
                link.addEventListener('click', function() {
                    navLinks.classList.remove('open');
                    toggleBtn.classList.remove('active');
                    toggleBtn.setAttribute('aria-expanded', 'false');
                });
            });

// ── Hero Parallax ──
            const heroParallax = document.getElementById('hero-parallax');
            window.addEventListener('scroll', function() {
                const scrollY = window.scrollY;
                const hero = document.querySelector('.hero');
                const heroHeight = hero.offsetHeight;
                if (scrollY <= heroHeight) {
                    const translateY = scrollY * 0.25;
                    heroParallax.style.transform = 'translateY(' + translateY + 'px) scale(1.05)';
                }
            });

// ── Intersection Observer for reveals ──
            const observerOptions = {
                threshold: 0.1,
                rootMargin: '0px 0px -40px 0px'
            };

const observer = new IntersectionObserver(function(entries) {
                entries.forEach(function(entry) {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                        // If it's a stagger container, stagger its children
                        if (entry.target.classList.contains('stagger-parent')) {
                            const items = entry.target.querySelectorAll('.stagger-item');
                            items.forEach(function(item, index) {
                                setTimeout(function() {
                                    item.classList.add('visible');
                                }, index * 120);
                            });
                        }
                    }
                });
            }, observerOptions);

// Observe all reveal elements
            document.querySelectorAll('.reveal, .reveal-left, .reveal-right, .reveal-scale').forEach(function(el) {
                observer.observe(el);
            });

// Observe stagger items directly if not inside stagger-parent
            document.querySelectorAll('.stagger-item').forEach(function(el) {
                // Check if it's inside a stagger-parent
                if (!el.closest('.stagger-parent')) {
                    observer.observe(el);
                }
            });

// Handle stagger-parent separately
            document.querySelectorAll('.stagger-parent').forEach(function(el) {
                observer.observe(el);
            });

// Also observe highlight cards, menu items, etc. that use stagger-item
            // We'll use a separate approach: observe all stagger-items with a staggered delay
            const staggerObserver = new IntersectionObserver(function(entries) {
                entries.forEach(function(entry) {
                    if (entry.isIntersecting) {
                        const items = entry.target.closest('.grid') ? entry.target.closest('.grid')
                            .querySelectorAll('.stagger-item') : [entry.target];
                        if (entry.target.closest('.grid')) {
                            // Handled by the grid's stagger-parent or direct observation
                        }
                        entry.target.classList.add('visible');
                    }
                });
            }, observerOptions);

// Direct observation for stagger items not in parent
            document.querySelectorAll('.stagger-item:not(.stagger-parent .stagger-item)').forEach(function(el) {
                staggerObserver.observe(el);
            });

// ── Stagger items in grids: observe the grid and stagger children ──
            document.querySelectorAll('.grid').forEach(function(grid) {
                const items = grid.querySelectorAll('.stagger-item');
                if (items.length > 0) {
                    const gridObserver = new IntersectionObserver(function(entries) {
                        entries.forEach(function(entry) {
                            if (entry.isIntersecting) {
                                const children = entry.target.querySelectorAll('.stagger-item');
                                children.forEach(function(item, index) {
                                    setTimeout(function() {
                                        item.classList.add('visible');
                                    }, index * 100);
                                });
                                gridObserver.unobserve(entry.target);
                            }
                        });
                    }, observerOptions);
                    gridObserver.observe(grid);
                }
            });

// ── Testimonials Carousel ──
            const testimonialData = [{
                text: '"The most incredible coffee experience. Every drink is crafted with such care and intention. It\'s my happy place."',
                author: 'Sarah M.',
                role: 'Regular'
            }, {
                text: '"I drive 30 minutes just for their Honey Lavender Latte. Absolutely worth it. The atmosphere is unmatched."',
                author: 'David L.',
                role: 'Loyal Customer'
            }, {
                text: '"We hosted our book club here and it was perfect. The staff treated us like family. Already planning our next visit."',
                author: 'Emma R.',
                role: 'Event Host'
            }, {
                text: '"As a remote worker, I\'ve tried every café in town. Brew & Co. has the best WiFi, best coffee, and best energy."',
                author: 'James K.',
                role: 'Digital Nomad'
            }];

let currentTestimonial = 0;
            const testimonialText = document.getElementById('testimonial-text');
            const testimonialAuthor = document.getElementById('testimonial-author');
            const testimonialStars = document.getElementById('testimonial-stars');
            const dotsContainer = document.getElementById('testimonial-dots');

function buildDots() {
                dotsContainer.innerHTML = '';
                testimonialData.forEach(function(_, i) {
                    const btn = document.createElement('button');
                    btn.setAttribute('role', 'tab');
                    btn.setAttribute('aria-label', 'Testimonial ' + (i + 1));
                    if (i === 0) btn.classList.add('active');
                    btn.addEventListener('click', function() {
                        goToTestimonial(i);
                    });
                    dotsContainer.appendChild(btn);
                });
            }
            buildDots();

function goToTestimonial(index) {
                currentTestimonial = index;
                const data = testimonialData[index];
                testimonialText.textContent = data.text;
                testimonialAuthor.innerHTML = '— ' + data.author + ' <span>' + data.role + '</span>';
                // Update dots
                const dots = dotsContainer.querySelectorAll('button');
                dots.forEach(function(dot, i) {
                    dot.classList.toggle('active', i === index);
                });
                // Animate
                const card = document.getElementById('testimonial-card');
                card.style.opacity = '0';
                card.style.transform = 'translateY(10px)';
                setTimeout(function() {
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, 150);
            }

let testimonialInterval = setInterval(function() {
                const next = (currentTestimonial + 1) % testimonialData.length;
                goToTestimonial(next);
            }, 5000);

// Pause on hover
            const testimonialCard = document.getElementById('testimonial-card');
            testimonialCard.addEventListener('mouseenter', function() {
                clearInterval(testimonialInterval);
            });
            testimonialCard.addEventListener('mouseleave', function() {
                testimonialInterval = setInterval(function() {
                    const next = (currentTestimonial + 1) % testimonialData.length;
                    goToTestimonial(next);
                }, 5000);
            });

// ── Menu Tabs ──
            const tabButtons = document.querySelectorAll('[data-tab]');
            const menuItems = document.querySelectorAll('.menu-grid .menu-item');

tabButtons.forEach(function(btn) {
                btn.addEventListener('click', function() {
                    const tab = btn.getAttribute('data-tab');
                    tabButtons.forEach(function(b) {
                        b.classList.remove('active');
                        b.setAttribute('aria-selected', 'false');
                    });
                    btn.classList.add('active');
                    btn.setAttribute('aria-selected', 'true');

menuItems.forEach(function(item) {
                        const category = item.getAttribute('data-category');
                        if (tab === category) {
                            item.classList.remove('hidden-item');
                            item.style.opacity = '0';
                            item.style.transform = 'translateY(20px)';
                            setTimeout(function() {
                                item.style.opacity = '1';
                                item.style.transform = 'translateY(0)';
                            }, 80);
                        } else {
                            item.classList.add('hidden-item');
                        }
                    });
                });
            });

// ── FAQ Accordion ──
            const faqItems = document.querySelectorAll('.faq-item');
            faqItems.forEach(function(item) {
                const question = item.querySelector('.faq-question');
                const answer = item.querySelector('.faq-answer');
                const icon = question.querySelector('.icon');

question.addEventListener('click', function() {
                    const isOpen = answer.classList.contains('open');
                    // Close all others
                    faqItems.forEach(function(other) {
                        const otherAnswer = other.querySelector('.faq-answer');
                        const otherIcon = other.querySelector('.icon');
                        if (other !== item) {
                            otherAnswer.classList.remove('open');
                            otherIcon.classList.remove('open');
                            other.querySelector('.faq-question').setAttribute('aria-expanded', 'false');
                        }
                    });
                    // Toggle this one
                    if (isOpen) {
                        answer.classList.remove('open');
                        icon.classList.remove('open');
                        question.setAttribute('aria-expanded', 'false');
                    } else {
                        answer.classList.add('open');
                        icon.classList.add('open');
                        question.setAttribute('aria-expanded', 'true');
                    }
                });
            });

// ── Contact Form ──
            const contactForm = document.getElementById('contact-form');
            const formSubmit = document.getElementById('form-submit');
            const formSuccess = document.getElementById('form-success');

contactForm.addEventListener('submit', function(e) {
                e.preventDefault();
                // Basic validation
                const name = document.getElementById('form-name').value.trim();
                const email = document.getElementById('form-email').value.trim();
                const message = document.getElementById('form-message').value.trim();

if (!name || !email || !message) {
                    alert('Please fill in all required fields.');
                    return;
                }
                if (!email.includes('@')) {
                    alert('Please enter a valid email address.');
                    return;
                }

// Simulate sending
                formSubmit.disabled = true;
                formSubmit.innerHTML = '<span class="spinner"></span>Sending...';
                setTimeout(function() {
                    formSuccess.classList.add('show');
                    formSubmit.disabled = false;
                    formSubmit.textContent = 'Send Message';
                    contactForm.reset();
                    setTimeout(function() {
                        formSuccess.classList.remove('show');
                    }, 5000);
                }, 1500);
            });

// ── Newsletter ──
            const newsletterForm = document.getElementById('newsletter-form');
            const newsletterMsg = document.getElementById('newsletter-msg');

newsletterForm.addEventListener('submit', function(e) {
                e.preventDefault();
                const input = newsletterForm.querySelector('input');
                if (input.value.trim() && input.value.includes('@')) {
                    newsletterMsg.textContent = '✓ You\'re in! Welcome to the Brew & Co. family.';
                    newsletterMsg.style.color = 'rgba(255,248,240,0.6)';
                    input.value = '';
                    setTimeout(function() {
                        newsletterMsg.textContent = '';
                    }, 4000);
                } else {
                    newsletterMsg.textContent = 'Please enter a valid email.';
                    newsletterMsg.style.color = '#E8C97A';
                }
            });

// ── Lightbox ──
            window.openLightbox = function(src) {
                const lightbox = document.getElementById('lightbox');
                const img = document.getElementById('lightbox-img');
                img.src = src;
                lightbox.classList.add('open');
                document.body.style.overflow = 'hidden';
            };

const lightbox = document.getElementById('lightbox');
            const lightboxClose = document.getElementById('lightbox-close');
            lightboxClose.addEventListener('click', function() {
                lightbox.classList.remove('open');
                document.body.style.overflow = '';
            });
            lightbox.addEventListener('click', function(e) {
                if (e.target === lightbox) {
                    lightbox.classList.remove('open');
                    document.body.style.overflow = '';
                }
            });
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape' && lightbox.classList.contains('open')) {
                    lightbox.classList.remove('open');
                    document.body.style.overflow = '';
                }
            });

// ── Smooth scroll for anchor links ──
            document.querySelectorAll('a[href^="#"]').forEach(function(anchor) {
                anchor.addEventListener('click', function(e) {
                    const targetId = anchor.getAttribute('href');
                    if (targetId && targetId.length > 1) {
                        const target = document.querySelector(targetId);
                        if (target) {
                            e.preventDefault();
                            target.scrollIntoView({ behavior: 'smooth', block: 'start' });
                        }
                    }
                });
            });

// ── Scroll-triggered parallax for hero ──
            // already handled above

// ── Keyboard accessibility for FAQ ──
            document.querySelectorAll('.faq-question').forEach(function(btn) {
                btn.addEventListener('keydown', function(e) {
                    if (e.key === 'Enter' || e.key === ' ') {
                        e.preventDefault();
                        btn.click();
                    }
                });
            });

// ── Lazy load images with Intersection Observer ──
            if ('loading' in HTMLImageElement.prototype) {
                // Native lazy loading is already used
            } else {
                // Fallback: observe images
                const imgObserver = new IntersectionObserver(function(entries) {
                    entries.forEach(function(entry) {
                        if (entry.isIntersecting) {
                            const img = entry.target;
                            if (img.dataset.src) {
                                img.src = img.dataset.src;
                            }
                            imgObserver.unobserve(img);
                        }
                    });
                });
                document.querySelectorAll('img[loading="lazy"]').forEach(function(img) {
                    if (!img.src && img.dataset.src) {
                        imgObserver.observe(img);
                    }
                });
            }

// ── Mobile menu: close on escape ──
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape' && navLinks.classList.contains('open')) {
                    navLinks.classList.remove('open');
                    toggleBtn.classList.remove('active');
                    toggleBtn.setAttribute('aria-expanded', 'false');
                }
            });

// ── Active nav link highlight on scroll ──
            const sections = document.querySelectorAll('section[id]');
            const navLinksArray = document.querySelectorAll('[data-nav]');

function updateActiveNav() {
                let current = '';
                sections.forEach(function(section) {
                    const sectionTop = section.offsetTop - 120;
                    if (window.scrollY >= sectionTop) {
                        current = section.getAttribute('id');
                    }
                });
                navLinksArray.forEach(function(link) {
                    const href = link.getAttribute('href').replace('#', '');
                    if (href === current) {
                        link.style.color = 'var(--warm-brown)';
                    } else {
                        link.style.color = '';
                    }
                });
            }
            window.addEventListener('scroll', updateActiveNav);
            updateActiveNav();

// ── Initial stagger for hero buttons ──
            // Already handled by CSS animations

console.log('☕ Brew & Co. — Crafted with love.');
        })();
    </script>

</body>
</html>
