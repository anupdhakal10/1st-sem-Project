//CODES FOR ONLINE MOVIE TICKET BOOKING SYSTEM
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>CineBook — Movie Ticketing</title>

    <style>
        :root {
            --background: #0f172a;
            --surface: #1e293b;
            --surface-hover: #334155;
            --primary: #6366f1;
            --primary-hover: #4f46e5;
            --accent: #f43f5e;
            --success: #10b981;
            --text: #f8fafc;
            --muted: #94a3b8;
            --border: #334155;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }

        body {
            background-color: var(--background);
            color: var(--text);
            padding-bottom: 60px;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 16px 24px;
            background: rgba(30, 41, 59, 0.95);
            backdrop-filter: blur(8px);
            border-bottom: 1px solid var(--border);
            position: sticky;
            top: 0;
            z-index: 10;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
        }

        .logo {
            font-size: 24px;
            font-weight: 800;
            letter-spacing: 1px;
            cursor: pointer;
            color: #fff;
        }

        .logo span {
            color: var(--accent);
        }

        .nav-menu {
            display: flex;
            gap: 24px;
            align-items: center;
        }

        .nav-link {
            color: var(--muted);
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            padding: 8px 12px;
            border-radius: 6px;
            transition: all 0.2s;
        }

        .nav-link:hover {
            color: #fff;
            background: rgba(99, 102, 241, 0.1);
        }

        .nav-link.active {
            color: var(--primary);
            background: rgba(99, 102, 241, 0.15);
        }

        .nav-buttons {
            display: flex;
            gap: 12px;
        }

        .page {
            display: none;
        }

        .page.active {
            display: block;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 10px 20px;
            font-weight: 600;
            font-size: 14px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            background: var(--surface);
            color: var(--text);
        }

        .btn-primary {
            background: var(--primary);
            color: #fff;
        }

        .btn-primary:hover:not(:disabled) {
            background: var(--primary-hover);
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(99, 102, 241, 0.3);
        }

        .btn-success {
            background: var(--success);
            color: #fff;
        }

        .btn-success:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(16, 185, 129, 0.3);
        }

        .btn-ghost {
            background: transparent;
            color: var(--muted);
        }

        .btn-ghost:hover {
            color: #fff;
            background: rgba(255, 255, 255, 0.05);
        }

        .btn-outline {
            background: transparent;
            border: 1px solid var(--border);
            color: var(--text);
        }

        .btn-outline:hover {
            background: var(--surface);
            border-color: var(--muted);
        }

        .btn-sm {
            padding: 6px 12px;
            font-size: 12px;
            border-radius: 6px;
        }

        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .hero {
            text-align: center;
            padding: 100px 24px;
            background: linear-gradient(135deg, #1e1b4b 0%, var(--background) 50%, #312e81 100%);
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 400px;
            height: 400px;
            background: radial-gradient(circle, rgba(99, 102, 241, 0.15), transparent);
            border-radius: 50%;
            top: -100px;
            right: -100px;
            pointer-events: none;
        }

        .hero h1 {
            font-size: 56px;
            font-weight: 900;
            margin-bottom: 16px;
            line-height: 1.1;
            position: relative;
            z-index: 1;
            background: linear-gradient(135deg, #fff, #cbd5e1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero h1 span {
            color: var(--accent);
            -webkit-text-fill-color: var(--accent);
        }

        .hero p {
            color: var(--muted);
            max-width: 600px;
            margin: 0 auto 32px;
            font-size: 16px;
            position: relative;
            z-index: 1;
        }

        .hero-btns {
            display: flex;
            gap: 12px;
            justify-content: center;
            position: relative;
            z-index: 1;
            flex-wrap: wrap;
        }

        .section {
            padding: 60px 24px;
            max-width: 1400px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 2px;
            color: var(--muted);
            margin-bottom: 32px;
            text-transform: uppercase;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .section-title::before {
            content: '';
            width: 32px;
            height: 2px;
            background: var(--primary);
            border-radius: 1px;
        }

        /* NEW: Date Filter Styles */
        .date-filter {
            display: flex;
            gap: 12px;
            margin-bottom: 32px;
            flex-wrap: wrap;
        }

        .date-btn {
            padding: 10px 20px;
            border-radius: 8px;
            border: 1px solid var(--border);
            background: var(--surface);
            color: var(--muted);
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s;
            font-size: 14px;
        }

        .date-btn:hover {
            border-color: var(--primary);
            color: #fff;
        }

        .date-btn.active {
            background: var(--primary);
            border-color: var(--primary);
            color: #fff;
        }

        .movies-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
            gap: 32px;
        }

        .movie-card {
            background: var(--surface);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--border);
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
            cursor: pointer;
        }

        .movie-card:hover {
            transform: translateY(-8px);
            border-color: var(--primary);
            box-shadow: 0 20px 40px rgba(99, 102, 241, 0.2);
        }

        /* MODIFIED: Movie Poster with Image Support */
        .movie-poster {
            position: relative;
            height: 380px;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
            padding: 16px;
            background-size: cover;
            background-position: center;
            background-color: #334155;
        }

        .movie-poster img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: 0;
        }

        .movie-date-badge {
            position: absolute;
            top: 12px;
            right: 12px;
            background: rgba(244, 63, 94, 0.9);
            padding: 8px 12px;
            border-radius: 6px;
            font-size: 12px;
            font-weight: 700;
            backdrop-filter: blur(8px);
            z-index: 3;
        }

        .movie-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to top, rgba(15, 23, 42, 0.95) 0%, rgba(15, 23, 42, 0.2) 70%);
            pointer-events: none;
            z-index: 1;
        }

        .movie-info {
            position: relative;
            z-index: 2;
        }

        .movie-title {
            font-size: 20px;
            font-weight: 800;
            color: #fff;
            margin-bottom: 4px;
            text-shadow: 0 2px 8px rgba(0, 0, 0, 0.6);
        }

        .movie-details {
            padding: 16px;
        }

        .movie-genre {
            font-size: 13px;
            color: var(--accent);
            font-weight: 600;
            margin-bottom: 6px;
        }

        .movie-meta {
            font-size: 13px;
            color: var(--muted);
            margin-bottom: 12px;
            display: flex;
            gap: 12px;
            flex-wrap: wrap;
        }

        .movie-meta span {
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .movie-showtimes-label {
            font-size: 11px;
            text-transform: uppercase;
            color: var(--muted);
            margin-bottom: 8px;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .movie-showtimes {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }

        .form-card {
            background: var(--surface);
            border: 1px solid var(--border);
            padding: 32px;
            border-radius: 12px;
            margin-bottom: 32px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
        }

        .form-card h3 {
            margin-bottom: 24px;
            font-size: 18px;
            color: #fff;
        }

        .form-group {
            margin-bottom: 16px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .form-group label {
            font-size: 12px;
            font-weight: 700;
            color: var(--muted);
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            background: var(--background);
            border: 1px solid var(--border);
            color: #fff;
            padding: 12px;
            border-radius: 8px;
            font-size: 14px;
            transition: all 0.2s;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 16px;
        }

        .admin-layout {
            display: flex;
            min-height: calc(100vh - 64px);
        }

        .admin-sidebar {
            width: 240px;
            background: #111827;
            border-right: 1px solid var(--border);
            padding: 16px;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .admin-nav-item {
            padding: 12px 16px;
            border-radius: 8px;
            cursor: pointer;
            color: var(--muted);
            font-weight: 500;
            font-size: 14px;
            transition: all 0.2s;
        }

        .admin-nav-item:hover,
        .admin-nav-item.active {
            background: var(--surface);
            color: #fff;
        }

        .admin-content {
            flex: 1;
            padding: 32px;
            overflow-y: auto;
        }

        .admin-section {
            display: none;
        }

        .admin-section.active {
            display: block;
        }

        .admin-section h2 {
            margin-bottom: 24px;
            font-size: 28px;
        }

        .table-wrap {
            width: 100%;
            overflow-x: auto;
            background: var(--surface);
            border-radius: 12px;
            border: 1px solid var(--border);
            margin-bottom: 32px;
        }

        .data-table {
            width: 100%;
            border-collapse: collapse;
            text-align: left;
            font-size: 14px;
        }

        .data-table th {
            background: rgba(0, 0, 0, 0.2);
            padding: 14px 16px;
            color: var(--muted);
            font-weight: 700;
            border-bottom: 1px solid var(--border);
            text-transform: uppercase;
            font-size: 12px;
            letter-spacing: 0.5px;
        }

        .data-table td {
            padding: 14px 16px;
            border-bottom: 1px solid var(--border);
            color: var(--muted);
        }

        /* NEW: Delete Button Styling */
        .delete-btn {
            background: var(--accent);
            color: #fff;
            border: none;
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 12px;
            transition: all 0.2s;
        }

        .delete-btn:hover {
            opacity: 0.8;
        }

        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(15, 23, 42, 0.8);
            backdrop-filter: blur(4px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            opacity: 0;
            pointer-events: none;
            transition: opacity 0.2s;
        }

        .modal-overlay.active {
            opacity: 1;
            pointer-events: auto;
        }

        .modal {
            background: var(--surface);
            width: 100%;
            max-width: 520px;
            border-radius: 16px;
            border: 1px solid var(--border);
            overflow: hidden;
            animation: slideUp 0.3s cubic-bezier(0.16, 1, 0.3, 1);
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            padding: 24px;
            border-bottom: 1px solid var(--border);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .modal-close {
            background: transparent;
            border: none;
            color: var(--muted);
            font-size: 20px;
            cursor: pointer;
            transition: all 0.2s;
        }

        .modal-close:hover {
            color: #fff;
        }

        .modal-body {
            padding: 24px;
        }

        .screen-label {
            text-align: center;
            background: linear-gradient(to bottom, rgba(99, 102, 241, 0.2), transparent);
            border-top: 3px solid var(--primary);
            padding: 12px 0;
            font-size: 12px;
            font-weight: 800;
            color: var(--primary);
            letter-spacing: 4px;
            margin-bottom: 24px;
            border-radius: 4px;
        }

        .seat-legend {
            display: flex;
            justify-content: center;
            gap: 24px;
            margin-bottom: 24px;
            font-size: 12px;
            color: var(--muted);
            flex-wrap: wrap;
        }

        .legend-item {
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .legend-dot {
            width: 16px;
            height: 16px;
            border-radius: 4px;
        }

        .legend-dot.available {
            background: #334155;
            border: 1px solid #475569;
        }

        .legend-dot.selected {
            background: var(--primary);
        }

        .legend-dot.booked {
            background: #0f172a;
            position: relative;
            border: 1px solid #1e293b;
        }

        .legend-dot.booked::after {
            content: '×';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            color: #64748b;
            font-size: 11px;
            font-weight: bold;
        }

        .seat-grid {
            display: grid;
            gap: 8px;
            justify-content: center;
            margin-bottom: 24px;
        }

        .seat {
            width: 36px;
            height: 36px;
            border-radius: 6px;
            font-size: 11px;
            font-weight: 600;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            user-select: none;
            transition: all 0.2s;
        }

        .seat.available {
            background: #334155;
            border: 1px solid #475569;
            color: #cbd5e1;
        }

        .seat.available:hover {
            background: #475569;
            transform: scale(1.08);
        }

        .seat.selected {
            background: var(--primary);
            color: #fff;
            border-color: var(--primary);
            transform: scale(1.1);
            box-shadow: 0 4px 12px rgba(99, 102, 241, 0.4);
        }

        .seat.booked {
            background: #0f172a;
            border: 1px solid #1e293b;
            color: #475569;
            cursor: not-allowed;
            position: relative;
        }

        .booking-summary {
            background: rgba(99, 102, 241, 0.08);
            padding: 16px;
            border-radius: 8px;
            border: 1px solid rgba(99, 102, 241, 0.2);
            margin-bottom: 20px;
        }

        .summary-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
            color: var(--muted);
        }

        .summary-row:last-child {
            margin-bottom: 0;
            padding-top: 12px;
            border-top: 1px dashed rgba(99, 102, 241, 0.3);
            font-weight: 700;
            color: #fff;
        }

        .booking-success {
            text-align: center;
        }

        .success-icon {
            font-size: 64px;
            margin-bottom: 16px;
            animation: bounce 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .success-title {
            font-size: 24px;
            font-weight: 900;
            color: var(--success);
            letter-spacing: 1px;
        }

        .content-section {
            max-width: 1200px;
            margin: 0 auto;
            padding: 60px 24px;
            line-height: 1.8;
        }

        .content-section h2 {
            font-size: 36px;
            margin-bottom: 24px;
            background: linear-gradient(135deg, #fff, #cbd5e1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .content-section p {
            color: var(--muted);
            margin-bottom: 16px;
            font-size: 16px;
        }

        .contact-form {
            max-width: 600px;
            margin-top: 32px;
        }

        .footer {
            background: #111827;
            border-top: 1px solid var(--border);
            padding: 40px 24px;
            text-align: center;
            color: var(--muted);
            font-size: 14px;
            margin-top: 60px;
        }

        #toast {
            position: fixed;
            bottom: 24px;
            right: 24px;
            background: #fff;
            color: #000;
            padding: 14px 24px;
            border-radius: 8px;
            font-weight: 600;
            font-size: 14px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
            z-index: 200;
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
            pointer-events: none;
        }

        #toast.show {
            opacity: 1;
            transform: translateY(0);
        }

        #toast.success {
            background: var(--success);
            color: #fff;
        }

        #toast.error {
            background: var(--accent);
            color: #fff;
        }

        @keyframes slideUp {
            from {
                transform: translateY(20px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        @media (max-width: 768px) {
            .form-row {
                grid-template-columns: 1fr;
            }

            .hero h1 {
                font-size: 36px;
            }

            .movies-grid {
                grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
                gap: 20px;
            }

            .nav-menu {
                gap: 12px;
                font-size: 13px;
            }

            .admin-layout {
                flex-direction: column;
            }

            .admin-sidebar {
                width: 100%;
                flex-direction: row;
                border-right: none;
                border-bottom: 1px solid var(--border);
                padding: 12px;
                gap: 4px;
                overflow-x: auto;
            }

            .admin-nav-item {
                padding: 10px 14px;
                font-size: 13px;
                white-space: nowrap;
            }

            /* NEW: Mobile date filter */
            .date-filter {
                flex-direction: column;
            }

            .date-btn {
                width: 100%;
            }
        }
    </style>
</head>

<body>

    <div id="toast"></div>

    <!-- Home Page -->
    <div id="page-home" class="page active">
        <header>
            <div class="logo" onclick="showPage('home')">CINE<span>BOOK</span></div>
            <div class="nav-menu">
                <div class="nav-link active" onclick="showPage('home')">🏠 Home</div>
                <div class="nav-link" onclick="scrollToMovies()">🎬 Movies</div>
                <div class="nav-link" onclick="showPage('about')">ℹ️ About</div>
                <div class="nav-link" onclick="showPage('contact')">📞 Contact</div>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-ghost btn-sm" onclick="showPage('admin-login')">🔐 Admin</button>
            </div>
        </header>

        <div class="hero">
            <h1>BOOK YOUR <span>SEAT.</span><br>OWN THE NIGHT.</h1>
            <p>Browse movies, pick your seats, and pay — all in one place.</p>
            <div class="hero-btns">
                <button class="btn btn-primary" onclick="scrollToMovies()">Browse Movies</button>
                <button class="btn btn-outline" onclick="showPage('about')">Learn More</button>
            </div>
        </div>

        <div class="section" id="movies-section">
            <div class="section-title">NOW SHOWING</div>
            <!-- NEW: Date Filter -->
            <div class="date-filter" id="user-date-filter">
                <button class="date-btn active" onclick="filterMoviesByDate(0)">📅 Today</button>
                <button class="date-btn" onclick="filterMoviesByDate(1)">📅 Tomorrow</button>
            </div>
            <div class="movies-grid" id="movies-grid"></div>
        </div>

        <div class="footer">
            <p>© 2026 CineBook. All rights reserved. | Designed for cinema enthusiasts 🎬</p>
        </div>
    </div>

    <!-- About Page -->
    <div id="page-about" class="page">
        <header>
            <div class="logo" onclick="showPage('home')">CINE<span>BOOK</span></div>
           
                <div class="nav-link" onclick="showPage('home')">🏠 Home</div>
                <div class="nav-link" onclick="showPage('home');setTimeout(scrollToMovies, 100)">🎬 Movies</div>
                <div class="nav-link active" onclick="showPage('about')">ℹ️ About</div>
                <div class="nav-link" onclick="showPage('contact')">📞 Contact</div>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-ghost btn-sm" onclick="showPage('admin-login')">🔐 Admin</button>
            </div>
        </header>

        <div class="content-section">
            <h2>About CineBook</h2>
            <p>CineBook is your ultimate movie ticketing platform, designed to make booking cinema seats fast, easy, and enjoyable. We've simplified the entire process so you can focus on what matters most — enjoying great movies.</p>
            
            <h2 style="margin-top: 40px; font-size: 24px;">Why Choose Us?</h2>
            <p>✨ <strong>Easy Booking</strong> - Intuitive interface for seamless seat selection<br>
            🎟️ <strong>Real-Time Updates</strong> - Always know seat availability<br>
            💳 <strong>Multiple Payment Options</strong> - Card, eSewa, Khalti, and more<br>
            🏆 <strong>Best Prices</strong> - Competitive rates and special offers<br>
            📱 <strong>Mobile Friendly</strong> - Book anytime, anywhere</p>

            <h2 style="margin-top: 40px; font-size: 24px;">Our Mission</h2>
            <p>To revolutionize the movie-going experience by providing a modern, reliable, and user-friendly platform for booking cinema tickets. We believe everyone deserves convenient access to entertainment.</p>
        </div>

        <div class="footer">
            <p>© 2026 CineBook. All rights reserved. | Making cinema accessible to all 🎬</p>
        </div>
    </div>

    <!-- Contact Page -->
    <div id="page-contact" class="page">
        <header>
            <div class="logo" onclick="showPage('home')">CINE<span>BOOK</span></div>
            <div class="nav-menu">
                <div class="nav-link" onclick="showPage('home')">🏠 Home</div>
                <div class="nav-link" onclick="showPage('home');setTimeout(scrollToMovies, 100)">🎬 Movies</div>
                <div class="nav-link" onclick="showPage('about')">ℹ️ About</div>
                <div class="nav-link active" onclick="showPage('contact')">📞 Contact</div>
            </div>
            <div class="nav-buttons">
                <button class="btn btn-ghost btn-sm" onclick="showPage('admin-login')">🔐 Admin</button>
            </div>
        </header>

        <div class="content-section">
            <h2>Get In Touch</h2>
            <p>Have questions? We'd love to hear from you. Reach out to us anytime!</p>

            <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 40px; margin-top: 40px;">
                <div>
                    <h3 style="color: var(--primary); margin-bottom: 16px;">Contact Information</h3>
                    <p>📍 <strong>Address:</strong><br>Kathmandu, Nepal</p>
                    <p style="margin-top: 16px;">📞 <strong>Phone:</strong><br>+977-1-XXXX-XXXX</p>
                    <p style="margin-top: 16px;">📧 <strong>Email:</strong><br>support@cinebook.com</p>
                    <p style="margin-top: 16px;">🕐 <strong>Hours:</strong><br>Mon-Sun: 9:00 AM - 10:00 PM</p>
                </div>

                <div class="contact-form">
                    <h3 style="color: var(--primary); margin-bottom: 16px;">Send us a Message</h3>
                    <div class="form-group">
                        <label>Name</label>
                        <input type="text" id="contact-name" placeholder="Your Name" />
                    </div>
                    <div class="form-group">
                        <label>Email</label>
                        <input type="email" id="contact-email" placeholder="your@email.com" />
                    </div>
                    <div class="form-group">
                        <label>Message</label>
                        <textarea id="contact-message" placeholder="Your message..." style="resize: vertical; min-height: 120px;"></textarea>
                    </div>
                    <button class="btn btn-primary" style="width: 100%;" onclick="sendContactMessage()">Send Message</button>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>© 2026 CineBook. We're here to help! 🎬</p>
        </div>
    </div>

    <!-- Admin Login Page -->
    <div id="page-admin-login" class="page">
        <header>
            <div class="logo" onclick="showPage('home')">CINE<span>BOOK</span></div>
        </header>
        <div style="display:flex;align-items:center;justify-content:center;min-height:calc(100vh - 64px);padding:24px">
            <div style="width:100%;max-width:380px">
                <div style="text-align:center;margin-bottom:32px">
                    <div style="font-size:36px;font-weight:900;letter-spacing:2px;color:var(--accent)">🔐 ADMIN</div>
                    <p style="color:var(--muted);font-size:14px;margin-top:8px">Access the cinema management panel</p>
                </div>
                <div class="form-card">
                    <div class="form-group">
                        <label>Username</label>
                        <input type="text" id="admin-user" placeholder="admin" value="admin" />
                    </div>
                    <div class="form-group">
                        <label>Password</label>
                        <input type="password" id="admin-pass" placeholder="••••••••" value="admin123"
                            onkeydown="if(event.key==='Enter')adminLogin()" />
                    </div>
                    <button class="btn btn-primary" style="width:100%;padding:12px" onclick="adminLogin()">Sign In</button>
                    <p style="text-align:center;font-size:12px;color:var(--muted);margin-top:14px">Default: admin / admin123</p>
                </div>
                <button class="btn btn-ghost btn-sm" onclick="showPage('home')" style="display:block;margin:0 auto">← Back to Home</button>
            </div>
        </div>
    </div>

    <!-- Admin Panel Page -->
    <div id="page-admin" class="page">
        <header>
            <div class="logo" onclick="showPage('home')">CINE<span>BOOK</span></div>
            <div class="nav-menu">
                <span style="color:var(--muted);font-size:13px;margin-right:8px">🔒 Admin Panel</span>
                <button class="btn btn-ghost btn-sm" onclick="showPage('home')">← User Side</button>
                <button class="btn btn-ghost btn-sm" onclick="adminLogout()">Logout</button>
            </div>
        </header>
        <div class="admin-layout">
            <div class="admin-sidebar">
                <div class="admin-nav-item active" onclick="switchAdminTab('movies')" id="tab-movies">🎬 Movies</div>
                <div class="admin-nav-item" onclick="switchAdminTab('bookings')" id="tab-bookings">🎟 Bookings</div>
            </div>
            <div class="admin-content">

                <!-- Movies Management Section -->
                <div class="admin-section active" id="admin-movies">
                    <h2>🎬 Manage Movies</h2>
                    <div class="form-card">
                        <h3>Add New Movie</h3>
                        <div class="form-row" style="margin-top: 16px;">
                            <div class="form-group">
                                <label>Movie Title</label>
                                <input type="text" id="m-title" placeholder="e.g. Inception" />
                            </div>
                            <div class="form-group">
                                <label>Genre</label>
                                <input type="text" id="m-genre" placeholder="e.g. Sci-Fi, Thriller" />
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label>Duration (mins)</label>
                                <input type="number" id="m-duration" placeholder="148" min="1" />
                            </div>
                            <div class="form-group">
                                <label>Ticket Price (NPR)</label>
                                <input type="number" id="m-price" placeholder="450" min="1" />
                            </div>
                        </div>
                        <div class="form-group">
                            <label>Showtimes (comma separated)</label>
                            <input type="text" id="m-showtimes" placeholder="10:00 AM, 2:00 PM, 7:30 PM" />
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label>Rows of Seats</label>
                                <input type="number" id="m-rows" placeholder="6" min="1" max="15" />
                            </div>
                            <div class="form-group">
                                <label>Seats per Row</label>
                                <input type="number" id="m-cols" placeholder="10" min="1" max="20" />
                            </div>
                        </div>
                        <div class="form-group">
                            <label>Movie Poster Image URL</label>
                            <input type="url" id="m-poster" placeholder="https://images.unsplash.com/...jpg" />
                        </div>
                        <!-- NEW: Show Date Selection -->
                        <div class="form-group">
                            <label>Show Date</label>
                            <select id="m-date">
                                <option value="0">Today</option>
                                <option value="1">Tomorrow</option>
                            </select>
                        </div>
                        <button class="btn btn-primary" onclick="addMovie()" style="width: 100%; padding: 12px; margin-top: 8px;">+ Add Movie</button>
                    </div>

                    <div class="table-wrap">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Movie</th>
                                    <th>Genre</th>
                                    <th>Duration</th>
                                    <th>Price</th>
                                    <th>Date</th>
                                    <th>Seats</th>
                                    <th>Showtimes</th>
                                    <th>Action</th>
                                </tr>
                            </thead>
                            <tbody id="admin-movies-list">
                                <tr>
                                    <td colspan="8" style="text-align:center;color:var(--muted);padding:32px">No movies added yet</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>

                <!-- Bookings Management Section -->
                <div class="admin-section" id="admin-bookings">
                    <h2>🎟️ All Bookings</h2>
                    <div class="table-wrap">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Booking ID</th>
                                    <th>Name</th>
                                    <th>Movie</th>
                                    <th>Showtime</th>
                                    <th>Seats</th>
                                    <th>Total</th>
                                    <th>Status</th>
                                </tr>
                            </thead>
                            <tbody id="admin-bookings-list">
                                <tr>
                                    <td colspan="7" style="text-align:center;color:var(--muted);padding:32px">No bookings yet</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Seat Selection Modal -->
    <div class="modal-overlay" id="modal-seats">
        <div class="modal">
            <div class="modal-header">
                <div>
                    <h2 id="seat-modal-title">Select Seats</h2>
                    <p style="color:var(--muted);font-size:13px;margin-top:4px" id="seat-modal-sub"></p>
                </div>
                <button class="modal-close" onclick="closeModal('modal-seats')">✕</button>
            </div>
            <div class="modal-body">
                <div class="screen-label">SCREEN</div>
                <div class="seat-legend">
                    <div class="legend-item">
                        <div class="legend-dot available"></div> Available
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot selected"></div> Selected
                    </div>
                    <div class="legend-item">
                        <div class="legend-dot booked"></div> Booked
                    </div>
                </div>
                <div class="seat-grid" id="seat-grid"></div>
                <div class="booking-summary" id="booking-summary" style="display:none">
                    <div class="summary-row"><span>Selected seats</span><span id="sum-seats">—</span></div>
                    <div class="summary-row"><span>Price per seat</span><span id="sum-price">—</span></div>
                    <div class="summary-row"><span>Total</span><span id="sum-total">—</span></div>
                </div>
                <button class="btn btn-primary" style="width:100%;padding:12px;margin-top:8px" onclick="proceedToPayment()"
                    id="btn-proceed" disabled>Select seats to continue</button>
            </div>
        </div>
    </div>

    <!-- Payment Modal -->
    <div class="modal-overlay" id="modal-payment">
        <div class="modal">
            <div class="modal-header">
                <div>
                    <h2>💳 Payment</h2>
                    <p style="color:var(--muted);font-size:13px;margin-top:4px" id="pay-modal-sub"></p>
                </div>
                <button class="modal-close" onclick="closeModal('modal-payment')">✕</button>
            </div>
            <div class="modal-body">
                <div
                    style="font-size:13px;font-weight:600;color:var(--muted);letter-spacing:1px;text-transform:uppercase;margin-bottom:14px">
                    Your Details</div>
                <div class="form-row">
                    <div class="form-group"><label>Full Name</label><input type="text" id="pay-name"
                            placeholder="Ram Bahadur" /></div>
                    <div class="form-group"><label>Email</label><input type="email" id="pay-email"
                            placeholder="ram@email.com" /></div>
                </div>
                <div class="form-group"><label>Phone</label><input type="tel" id="pay-phone"
                        placeholder="+977 98XXXXXXXX" maxlength="10" /></div>

                <div
                    style="font-size:13px;font-weight:600;color:var(--muted);letter-spacing:1px;text-transform:uppercase;margin:20px 0 14px">
                    Payment Method</div>
                <div class="form-group">
                    <label>Method</label>
                    <select id="pay-method" onchange="togglePaymentFields()">
                        <option value="card">Credit / Debit Card</option>
                        <option value="esewa">eSewa</option>
                        <option value="khalti">Khalti</option>
                        <option value="connectips">ConnectIPS</option>
                    </select>
                </div>

                <div id="card-fields">
                    <div class="form-group"><label>Card Number</label><input type="text" id="pay-card"
                            placeholder="4242 4242 4242 4242" maxlength="19" oninput="formatCard(this)" /></div>
                    <div class="form-row">
                        <div class="form-group"><label>Expiry</label><input type="text" id="pay-expiry"
                                placeholder="MM / YY" maxlength="7" oninput="formatExpiry(this)" /></div>
                        <div class="form-group"><label>CVV</label><input type="text" id="pay-cvv" placeholder="123"
                                maxlength="4" /></div>
                    </div>
                    <div class="form-group"><label>Cardholder Name</label><input type="text" id="pay-cardholder"
                            placeholder="RAM BAHADUR" /></div>
                </div>

                <div id="wallet-fields" style="display:none">
                    <div class="form-group"><label id="wallet-label">eSewa ID / Mobile</label><input type="text"
                            id="pay-wallet" placeholder="9800000000" maxlength="10" /></div>
                </div>

                <div class="booking-summary" style="margin-top:20px">
                    <div class="summary-row"><span>Movie</span><span id="pay-sum-movie">—</span></div>
                    <div class="summary-row"><span>Showtime</span><span id="pay-sum-time">—</span></div>
                    <div class="summary-row"><span>Seats</span><span id="pay-sum-seats">—</span></div>
                    <div class="summary-row"><span>Total Amount</span><span id="pay-sum-total">—</span></div>
                </div>

                <button class="btn btn-success" style="width:100%;padding:12px;margin-top:8px;font-size:15px"
                    onclick="confirmPayment()">✓ Confirm & Pay</button>
                <p style="text-align:center;font-size:11px;color:var(--muted);margin-top:10px">🔒 This is a demo. No
                    real payment is processed.</p>
            </div>
        </div>
    </div>

    <!-- Success Modal -->
    <div class="modal-overlay" id="modal-success">
        <div class="modal" style="max-width:460px">
            <div class="modal-header" style="justify-content:flex-end">
                <button class="modal-close" onclick="closeModal('modal-success');showPage('home')">✕</button>
            </div>
            <div class="modal-body booking-success">
                <div class="success-icon">🎉</div>
                <div class="success-title">BOOKING CONFIRMED!</div>
                <p style="color:var(--muted);margin-top:8px;font-size:14px">Your seats are reserved. Enjoy the movie!</p>
                <div class="ticket-card" id="ticket-card"></div>
                <button class="btn btn-primary" style="margin-top:16px;width:100%"
                    onclick="closeModal('modal-success');showPage('home')">← Back to Movies</button>
            </div>
        </div>
    </div>

    <script>
        // ========== APPLICATION STATE ==========
        window.CineBookState = {
            movies: [],
            bookings: [],
            currentBooking: { movieId: null, showtime: null, selectedSeats: [], dateOffset: 0 },
            isAdmin: false,
            currentDateFilter: 0
        };

        // ========== DEFAULT MOVIES DATA (11 Movies with Image URLs and Date Offsets) ==========
        const defaultMovies = [
            {
                id: "m-1",
                title: "Dune: Part Two",
                genre: "Sci-Fi, Adventure",
                duration: 166,
                price: 500,
                showtimes: ["11:00 AM", "3:00 PM", "8:00 PM"],
                rows: 8,
                cols: 12,
                poster: "https://images.unsplash.com/photo-1534447677768-be436bb09401?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "11:00 AM": ["C-4", "C-5"], "3:00 PM": [], "8:00 PM": ["F-6"] }
            },
            {
                id: "m-2",
                title: "Oppenheimer",
                genre: "Biography, Drama",
                duration: 180,
                price: 450,
                showtimes: ["10:00 AM", "2:15 PM", "7:00 PM"],
                rows: 7,
                cols: 10,
                poster: "https://images.unsplash.com/photo-1446776653964-20c1d3a81b06?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "10:00 AM": [], "2:15 PM": ["A-1", "A-2"], "7:00 PM": [] }
            },
            {
                id: "m-3",
                title: "Spider-Man: Across the Spider-Verse",
                genre: "Animation, Action",
                duration: 140,
                price: 400,
                showtimes: ["12:00 PM", "4:30 PM"],
                rows: 6,
                cols: 10,
                poster: "https://images.unsplash.com/photo-1635805737707-575885ab0820?w=600&q=80",
                dateOffset: 1,
                bookedSeats: { "12:00 PM": ["B-5"], "4:30 PM": [] }
            },
            {
                id: "m-4",
                title: "The Batman",
                genre: "Action, Crime",
                duration: 176,
                price: 450,
                showtimes: ["1:00 PM", "6:30 PM"],
                rows: 8,
                cols: 12,
                poster: "https://images.unsplash.com/photo-1509248961158-e54f6934749c?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "1:00 PM": [], "6:30 PM": ["D-6", "D-7"] }
            },
            {
                id: "m-5",
                title: "Top Gun: Maverick",
                genre: "Action, Drama",
                duration: 130,
                price: 500,
                showtimes: ["11:30 AM", "3:45 PM", "8:15 PM"],
                rows: 7,
                cols: 11,
                poster: "https://images.unsplash.com/photo-1518770660439-4636190af475?w=600&q=80",
                dateOffset: 1,
                bookedSeats: { "11:30 AM": [], "3:45 PM": [], "8:15 PM": [] }
            },
            {
                id: "m-6",
                title: "Avatar: The Way of Water",
                genre: "Sci-Fi, Adventure",
                duration: 192,
                price: 550,
                showtimes: ["10:30 AM", "2:45 PM", "7:30 PM"],
                rows: 8,
                cols: 12,
                poster: "https://images.unsplash.com/photo-1504384308090-c894fdcc538d?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "10:30 AM": ["E-3"], "2:45 PM": [], "7:30 PM": ["G-8"] }
            },
            {
                id: "m-7",
                title: "Black Panther: Wakanda Forever",
                genre: "Action, Adventure",
                duration: 161,
                price: 450,
                showtimes: ["12:30 PM", "5:00 PM", "9:00 PM"],
                rows: 7,
                cols: 10,
                poster: "https://images.unsplash.com/photo-1606112219348-204d7d8b94ee?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "12:30 PM": [], "5:00 PM": ["C-2", "C-3"], "9:00 PM": [] }
            },
            {
                id: "m-8",
                title: "The Flash",
                genre: "Action, Sci-Fi",
                duration: 144,
                price: 400,
                showtimes: ["1:30 PM", "6:00 PM"],
                rows: 6,
                cols: 10,
                poster: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?w=600&q=80",
                dateOffset: 1,
                bookedSeats: { "1:30 PM": [], "6:00 PM": ["B-7", "B-8"] }
            },
            {
                id: "m-9",
                title: "Inception",
                genre: "Sci-Fi, Thriller",
                duration: 148,
                price: 500,
                showtimes: ["10:15 AM", "3:30 PM", "7:45 PM"],
                rows: 8,
                cols: 12,
                poster: "https://images.unsplash.com/photo-1440404653325-ab127d49abc1?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "10:15 AM": [], "3:30 PM": [], "7:45 PM": [] }
            },
            {
                id: "m-10",
                title: "Interstellar",
                genre: "Sci-Fi, Drama",
                duration: 169,
                price: 550,
                showtimes: ["9:30 AM", "2:00 PM", "8:30 PM"],
                rows: 8,
                cols: 12,
                poster: "https://images.unsplash.com/photo-1478720568477-152d9e3fb66d?w=600&q=80",
                dateOffset: 1,
                bookedSeats: { "9:30 AM": [], "2:00 PM": [], "8:30 PM": [] }
            },
            {
                id: "m-11",
                title: "The Shawshank Redemption",
                genre: "Drama, Crime",
                duration: 142,
                price: 450,
                showtimes: ["11:00 AM", "4:00 PM", "7:30 PM"],
                rows: 7,
                cols: 10,
                poster: "https://images.unsplash.com/photo-1485095329183-d0797cdc5676?w=600&q=80",
                dateOffset: 0,
                bookedSeats: { "11:00 AM": [], "4:00 PM": ["A-5"], "7:30 PM": [] }
            }
        ];

        // ========== HELPER FUNCTIONS ==========
        function getDateString(daysOffset = 0) {
            const date = new Date();
            date.setDate(date.getDate() + daysOffset);
            return date.toLocaleDateString('en-US', { month: 'short', day: 'numeric' });
        }

        function getDateLabel(daysOffset = 0) {
            if (daysOffset === 0) return "Today";
            if (daysOffset === 1) return "Tomorrow";
            return getDateString(daysOffset);
        }

        // ========== DATA PERSISTENCE ==========
        function loadData() {
            try {
                const localMovies = localStorage.getItem("cinebook_movies");
                const localBookings = localStorage.getItem("cinebook_bookings");
                
                if (localMovies) {
                    window.CineBookState.movies = JSON.parse(localMovies);
                } else {
                    window.CineBookState.movies = JSON.parse(JSON.stringify(defaultMovies));
                    saveData();
                }
                
                window.CineBookState.bookings = localBookings ? JSON.parse(localBookings) : [];
            } catch (error) {
                console.error("Error loading data:", error);
                window.CineBookState.movies = JSON.parse(JSON.stringify(defaultMovies));
                window.CineBookState.bookings = [];
                saveData();
            }
        }

        function saveData() {
            try {
                localStorage.setItem("cinebook_movies", JSON.stringify(window.CineBookState.movies));
                localStorage.setItem("cinebook_bookings", JSON.stringify(window.CineBookState.bookings));
            } catch (error) {
                console.error("Error saving data:", error);
                showToast("Failed to save data", "error");
            }
        }

        // ========== UI FUNCTIONS ==========
        function showToast(message, type = "success") {
            const toast = document.getElementById("toast");
            toast.innerText = message;
            toast.className = `show ${type}`;
            setTimeout(() => { toast.className = toast.className.replace("show", ""); }, 3000);
        }

        function showPage(pageId) {
            document.querySelectorAll(".page").forEach(page => page.classList.remove("active"));
            document.querySelectorAll(".nav-link").forEach(link => link.classList.remove("active"));
            
            const targetPage = document.getElementById(`page-${pageId}`);
            if (targetPage) {
                targetPage.classList.add("active");
                window.scrollTo({ top: 0, behavior: "instant" });
            }
            
            if (pageId === "home") {
                window.CineBookState.currentDateFilter = 0;
                renderUserMovies();
                document.querySelector(".nav-link[onclick*='home']")?.classList.add("active");
                updateDateButtons();
            }
            if (pageId === "admin") {
                if (!window.CineBookState.isAdmin) {
                    showPage("admin-login");
                    showToast("Please login to access the admin panel", "error");
                } else {
                    renderAdminMovies();
                    renderAdminBookings();
                }
            }
        }

        // NEW: Filter movies by date (0 = Today, 1 = Tomorrow)
        function filterMoviesByDate(dateOffset) {
            window.CineBookState.currentDateFilter = dateOffset;
            updateDateButtons();
            renderUserMovies();
        }

        // NEW: Update active state on date buttons
        function updateDateButtons() {
            document.querySelectorAll(".date-btn").forEach((btn, idx) => {
                btn.classList.toggle("active", idx === window.CineBookState.currentDateFilter);
            });
        }

        function scrollToMovies() {
            showPage('home');
            setTimeout(() => {
                document.getElementById('movies-section').scrollIntoView({ behavior: 'smooth' });
            }, 100);
        }

        function openModal(modalId) { document.getElementById(modalId)?.classList.add("active"); }
        function closeModal(modalId) { document.getElementById(modalId)?.classList.remove("active"); }

        // ========== RENDERING FUNCTIONS ==========
        // MODIFIED: renderUserMovies - filters by dateOffset and displays poster images
        function renderUserMovies() {
            const grid = document.getElementById("movies-grid");
            if (!grid) return;
            
            const filteredMovies = window.CineBookState.movies.filter(
                m => m.dateOffset === window.CineBookState.currentDateFilter
            );
            
            if (filteredMovies.length === 0) {
                grid.innerHTML = `<div style="grid-column: 1/-1; text-align: center; color: var(--muted); padding: 48px 0;">No movies available for this date.</div>`;
                return;
            }
            
            grid.innerHTML = filteredMovies.map(movie => {
                const timeButtons = movie.showtimes.map(t => `<button class="btn btn-sm btn-outline" onclick="selectShowtime('${movie.id}', '${t}', ${movie.dateOffset})">${t}</button>`).join("");
                const dateLabel = getDateLabel(movie.dateOffset);
                
                return `
                    <div class="movie-card">
                        <div class="movie-poster">
                            <img src="${movie.poster}" alt="${movie.title}" onerror="this.src='https://images.unsplash.com/photo-1533613220915-c3400ca199e7?w=600&q=80'" />
                            <div class="movie-date-badge">${dateLabel}</div>
                            <div class="movie-overlay"></div>
                            <div class="movie-info">
                                <div class="movie-title">${movie.title}</div>
                            </div>
                        </div>
                        <div class="movie-details">
                            <div class="movie-genre">${movie.genre}</div>
                            <div class="movie-meta">
                                <span>🕒 ${movie.duration} min</span>
                                <span>💵 NPR ${movie.price}</span>
                            </div>
                            <div class="movie-showtimes-label">Available Showtimes:</div>
                            <div class="movie-showtimes">${timeButtons}</div>
                        </div>
                    </div>`;
            }).join("");
        }

        // MODIFIED: selectShowtime - includes dateOffset parameter
        function selectShowtime(movieId, showtime, dateOffset) {
            window.CineBookState.currentBooking = { movieId, showtime, selectedSeats: [], dateOffset };
            openSeatModal();
        }

        function openSeatModal() {
            const booking = window.CineBookState.currentBooking;
            const movie = window.CineBookState.movies.find(m => m.id === booking.movieId);
            if (!movie) return;

            document.getElementById("seat-modal-title").innerText = movie.title;
            document.getElementById("seat-modal-sub").innerText = `${getDateLabel(booking.dateOffset)} • ${booking.showtime} | Main Screen`;
            document.getElementById("sum-price").innerText = `NPR ${movie.price}`;

            const gridContainer = document.getElementById("seat-grid");
            gridContainer.style.gridTemplateColumns = `repeat(${movie.cols}, minmax(30px, 1fr))`;
            gridContainer.innerHTML = "";

            const bookedList = movie.bookedSeats[booking.showtime] || [];

            for (let r = 0; r < movie.rows; r++) {
                const rowLetter = String.fromCharCode(65 + r);
                for (let c = 1; c <= movie.cols; c++) {
                    const seatId = `${rowLetter}-${c}`;
                    const seatDiv = document.createElement("div");
                    seatDiv.className = `seat ${bookedList.includes(seatId) ? 'booked' : 'available'}`;
                    seatDiv.innerText = seatId;

                    if (!bookedList.includes(seatId)) {
                        seatDiv.onclick = () => toggleSeatSelection(seatDiv, seatId, movie.price);
                    }
                    gridContainer.appendChild(seatDiv);
                }
            }
            updateBookingSummary(movie.price);
            openModal("modal-seats");
        }

        function toggleSeatSelection(element, seatId, price) {
            const selected = window.CineBookState.currentBooking.selectedSeats;
            const index = selected.indexOf(seatId);
            if (index > -1) {
                selected.splice(index, 1);
                element.className = "seat available";
            } else {
                selected.push(seatId);
                element.className = "seat selected";
            }
            updateBookingSummary(price);
        }

        function updateBookingSummary(price) {
            const selected = window.CineBookState.currentBooking.selectedSeats;
            const summaryBlock = document.getElementById("booking-summary");
            const proceedBtn = document.getElementById("btn-proceed");

            if (selected.length > 0) {
                summaryBlock.style.display = "block";
                document.getElementById("sum-seats").innerText = selected.join(", ");
                document.getElementById("sum-total").innerText = `NPR ${selected.length * price}`;
                proceedBtn.disabled = false;
                proceedBtn.innerText = `Proceed to Payment (${selected.length} Selected)`;
            } else {
                summaryBlock.style.display = "none";
                proceedBtn.disabled = true;
                proceedBtn.innerText = "Select seats to continue";
            }
        }

        function proceedToPayment() {
            closeModal("modal-seats");
            const booking = window.CineBookState.currentBooking;
            const movie = window.CineBookState.movies.find(m => m.id === booking.movieId);
            if (!movie) return;

            document.getElementById("pay-modal-sub").innerText = `${movie.title} • ${getDateLabel(booking.dateOffset)} • ${booking.showtime}`;
            document.getElementById("pay-sum-movie").innerText = movie.title;
            document.getElementById("pay-sum-time").innerText = booking.showtime;
            document.getElementById("pay-sum-seats").innerText = booking.selectedSeats.join(", ");
            document.getElementById("pay-sum-total").innerText = `NPR ${booking.selectedSeats.length * movie.price}`;

            document.getElementById("pay-name").value = "";
            document.getElementById("pay-email").value = "";
            document.getElementById("pay-phone").value = "";
            openModal("modal-payment");
        }

        function togglePaymentFields() {
            const method = document.getElementById("pay-method").value;
            document.getElementById("card-fields").style.display = method === "card" ? "block" : "none";
            document.getElementById("wallet-fields").style.display = method === "card" ? "none" : "block";
            if (method !== "card") {
                document.getElementById("wallet-label").innerText = `${method.toUpperCase()} ID / Mobile Number`;
            }
        }

        function formatCard(el) { el.value = el.value.replace(/\D/g, "").replace(/(.{4})/g, '$1 ').trim(); }
        function formatExpiry(el) { el.value = el.value.replace(/\D/g, "").replace(/(.{2})/, '$1 / ').substring(0, 7); }

        function confirmPayment() {
            const name = document.getElementById("pay-name").value.trim();
            const email = document.getElementById("pay-email").value.trim();
            const phone = document.getElementById("pay-phone").value.trim();
            
            if (!name || !email || !phone) {
                showToast("Please fill all information fields", "error");
                return;
            }

            const booking = window.CineBookState.currentBooking;
            const movie = window.CineBookState.movies.find(m => m.id === booking.movieId);
            const totalAmount = booking.selectedSeats.length * movie.price;
            const bookingId = "CB-" + Math.floor(100000 + Math.random() * 900000);

            const newBooking = {
                id: bookingId,
                customerName: name,
                customerEmail: email,
                customerPhone: phone,
                movieTitle: movie.title,
                movieId: movie.id,
                showtime: booking.showtime,
                seats: [...booking.selectedSeats],
                total: totalAmount,
                status: "Confirmed"
            };

            window.CineBookState.bookings.push(newBooking);
            if (!movie.bookedSeats[booking.showtime]) movie.bookedSeats[booking.showtime] = [];
            movie.bookedSeats[booking.showtime].push(...booking.selectedSeats);

            saveData();
            closeModal("modal-payment");

            document.getElementById("ticket-card").innerHTML = `
                <div style="background: rgba(255,255,255,0.05); border: 2px dashed rgba(99,102,241,0.4); border-radius: 8px; padding: 20px; margin-top: 20px; text-align: left; font-family: monospace; font-size: 13px;">
                    <div style="text-align: center; font-weight: bold; font-size: 14px; margin-bottom: 14px; color: var(--primary);">🎫 CINEBOOK DIGITAL TICKET</div>
                    <div style="display:flex; justify-content:space-between; margin-bottom:6px;"><span>TICKET ID:</span><span style="color:#fff;font-weight:700">${bookingId}</span></div>
                    <div style="display:flex; justify-content:space-between; margin-bottom:6px;"><span>MOVIE:</span><span style="color:#fff;font-weight:700">${movie.title}</span></div>
                    <div style="display:flex; justify-content:space-between; margin-bottom:6px;"><span>DATE:</span><span style="color:#fff;font-weight:700">${getDateLabel(booking.dateOffset)}</span></div>
                    <div style="display:flex; justify-content:space-between; margin-bottom:6px;"><span>SHOWTIME:</span><span style="color:#fff;font-weight:700">${booking.showtime}</span></div>
                    <div style="display:flex; justify-content:space-between; margin-bottom:6px;"><span>SEATS:</span><span style="color:#fff;font-weight:700">${booking.selectedSeats.join(", ")}</span></div>
                    <div style="display:flex; justify-content:space-between;"><span>PASSENGER:</span><span style="color:#fff;font-weight:700">${name}</span></div>
                </div>`;
            openModal("modal-success");
        }

        // ========== ADMIN FUNCTIONS ==========
        function adminLogin() {
            const user = document.getElementById("admin-user").value;
            const pass = document.getElementById("admin-pass").value;
            if (user === "admin" && pass === "admin123") {
                window.CineBookState.isAdmin = true;
                showToast("Welcome back, administrator!");
                showPage("admin");
            } else {
                showToast("Invalid credentials", "error");
            }
        }

        function adminLogout() {
            window.CineBookState.isAdmin = false;
            showToast("Logged out successfully");
            showPage("home");
        }

        function switchAdminTab(tabName) {
            document.querySelectorAll(".admin-nav-item").forEach(item => item.classList.remove("active"));
            document.querySelectorAll(".admin-section").forEach(sec => sec.classList.remove("active"));
            document.getElementById(`tab-${tabName}`).classList.add("active");
            document.getElementById(`admin-${tabName}`).classList.add("active");
        }

        // MODIFIED: addMovie - includes dateOffset handling
        function addMovie() {
            const title = document.getElementById("m-title").value.trim();
            const genre = document.getElementById("m-genre").value.trim();
            const duration = parseInt(document.getElementById("m-duration").value);
            const price = parseInt(document.getElementById("m-price").value);
            const rawTimes = document.getElementById("m-showtimes").value;
            const rows = parseInt(document.getElementById("m-rows").value);
            const cols = parseInt(document.getElementById("m-cols").value);
            const poster = document.getElementById("m-poster").value.trim();
            const dateOffset = parseInt(document.getElementById("m-date").value);

            if (!title || !genre || !duration || !price || !rawTimes || !rows || !cols) {
                showToast("Please provide all required fields", "error");
                return;
            }

            const showtimes = rawTimes.split(",").map(t => t.trim()).filter(t => t.length > 0);
            const bookedSeatsMap = {};
            showtimes.forEach(t => { bookedSeatsMap[t] = []; });

            const newMovie = {
                id: "m-" + Date.now(),
                title,
                genre,
                duration,
                price,
                showtimes,
                rows,
                cols,
                poster: poster || null,
                dateOffset,
                bookedSeats: bookedSeatsMap
            };

            window.CineBookState.movies.push(newMovie);
            saveData();

            // Clear form
            document.getElementById("m-title").value = "";
            document.getElementById("m-genre").value = "";
            document.getElementById("m-duration").value = "";
            document.getElementById("m-price").value = "";
            document.getElementById("m-showtimes").value = "";
            document.getElementById("m-poster").value = "";
            document.getElementById("m-date").value = "0";

            showToast("Movie added successfully!");
            renderAdminMovies();
        }

        function deleteMovie(movieId) {
            if (confirm("Are you sure you want to delete this movie?")) {
                window.CineBookState.movies = window.CineBookState.movies.filter(m => m.id !== movieId);
                saveData();
                renderAdminMovies();
                showToast("Movie deleted successfully");
            }
        }

        // MODIFIED: renderAdminMovies - displays dateOffset with color-coded badge
        function renderAdminMovies() {
            const container = document.getElementById("admin-movies-list");
            if (!container) return;
            
            if (window.CineBookState.movies.length === 0) {
                container.innerHTML = `<tr><td colspan="8" style="text-align:center;color:var(--muted);padding:32px">No movies added yet</td></tr>`;
                return;
            }
            
            container.innerHTML = window.CineBookState.movies.map(movie => `
                <tr>
                    <td><strong style="color:#fff">${movie.title}</strong></td>
                    <td>${movie.genre}</td>
                    <td>${movie.duration} min</td>
                    <td>NPR ${movie.price}</td>
                    <td><span style="background: ${movie.dateOffset === 0 ? 'rgba(16,185,129,0.2)' : 'rgba(99,102,241,0.2)'}; padding: 4px 8px; border-radius: 4px; font-size: 12px; font-weight: 600;">${getDateLabel(movie.dateOffset)}</span></td>
                    <td>${movie.rows} × ${movie.cols}</td>
                    <td style="font-size: 12px;">${movie.showtimes.join(", ")}</td>
                    <td>
                        <button class="delete-btn" onclick="deleteMovie('${movie.id}')">🗑️ Delete</button>
                    </td>
                </tr>`).join("");
        }

        function renderAdminBookings() {
            const container = document.getElementById("admin-bookings-list");
            if (!container) return;
            
            if (window.CineBookState.bookings.length === 0) {
                container.innerHTML = `<tr><td colspan="7" style="text-align:center;color:var(--muted);padding:32px">No bookings yet</td></tr>`;
                return;
            }
            
            container.innerHTML = window.CineBookState.bookings.map(b => `
                <tr>
                    <td><span style="font-family:monospace; color:var(--accent); font-weight: 700">${b.id}</span></td>
                    <td>${b.customerName}<br><small style="color:var(--muted)">${b.customerPhone}</small></td>
                    <td><strong>${b.movieTitle}</strong></td>
                    <td>${b.showtime}</td>
                    <td style="font-size: 12px;">${b.seats.join(", ")}</td>
                    <td style="color:var(--success);font-weight:600">NPR ${b.total}</td>
                    <td><span style="color:var(--success); font-size:12px; font-weight:700;">✓ ${b.status.toUpperCase()}</span></td>
                </tr>`).join("");
        }

        function sendContactMessage() {
            const name = document.getElementById("contact-name").value.trim();
            const email = document.getElementById("contact-email").value.trim();
            const message = document.getElementById("contact-message").value.trim();

            if (!name || !email || !message) {
                showToast("Please fill all fields", "error");
                return;
            }

            showToast(`Thank you, ${name}! We'll get back to you soon.`);
            document.getElementById("contact-name").value = "";
            document.getElementById("contact-email").value = "";
            document.getElementById("contact-message").value = "";
        }

        // ========== INITIALIZATION ==========
        loadData();
        window.addEventListener("DOMContentLoaded", () => { showPage("home"); });
    </script>

</body>

</html>
