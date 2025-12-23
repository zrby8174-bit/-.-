<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام نماذج الاختبارات التعليمية - النسخة الكاملة</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        /* الأساسيات */
        :root {
            --primary-color: #4361ee;
            --primary-dark: #3a0ca3;
            --secondary-color: #7209b7;
            --success-color: #2ecc71;
            --danger-color: #e74c3c;
            --warning-color: #f39c12;
            --info-color: #3498db;
            --light-bg: #f8f9fa;
            --dark-bg: #1a1a2e;
            --card-bg: #ffffff;
            --text-primary: #2d3436;
            --text-secondary: #636e72;
            --border-color: #e9ecef;
            --shadow: 0 4px 6px rgba(0,0,0,0.08);
            --shadow-hover: 0 10px 25px rgba(0,0,0,0.15);
            --transition: all 0.3s ease;
        }

        [data-theme="dark"] {
            --primary-color: #5a7dff;
            --light-bg: #1a1a2e;
            --dark-bg: #0f0f1a;
            --card-bg: #16213e;
            --text-primary: #ffffff;
            --text-secondary: #b0b0b0;
            --border-color: #2d3748;
            --shadow: 0 4px 6px rgba(0,0,0,0.3);
            --shadow-hover: 0 10px 25px rgba(0,0,0,0.5);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background-color: var(--light-bg);
            color: var(--text-primary);
            line-height: 1.6;
            transition: var(--transition);
            direction: rtl;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* شريط التنقل */
        .navbar {
            background-color: var(--card-bg);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
            transition: var(--transition);
        }

        .nav-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            height: 70px;
        }

        .nav-brand {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary-color);
        }

        .nav-brand i {
            font-size: 1.8rem;
        }

        .nav-menu {
            display: flex;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .nav-menu {
                display: none;
            }
        }

        .nav-link {
            text-decoration: none;
            color: var(--text-secondary);
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 8px 16px;
            border-radius: 8px;
            transition: var(--transition);
        }

        .nav-link:hover,
        .nav-link.active {
            color: var(--primary-color);
            background-color: rgba(67, 97, 238, 0.1);
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .btn-theme {
            background: none;
            border: none;
            font-size: 1.2rem;
            color: var(--text-primary);
            cursor: pointer;
            padding: 8px;
            border-radius: 50%;
            transition: var(--transition);
        }

        .btn-theme:hover {
            background-color: rgba(0, 0, 0, 0.05);
        }

        .btn-login {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: var(--transition);
        }

        .btn-login:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .btn-mobile-menu {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--text-primary);
            cursor: pointer;
        }

        @media (max-width: 768px) {
            .btn-mobile-menu {
                display: block;
            }
        }

        /* القائمة الجانبية للجوال */
        .mobile-sidebar {
            position: fixed;
            top: 0;
            right: -300px;
            width: 280px;
            height: 100vh;
            background-color: var(--card-bg);
            box-shadow: var(--shadow);
            z-index: 1001;
            padding: 80px 20px 20px;
            transition: right 0.3s ease;
        }

        .mobile-sidebar.active {
            right: 0;
        }

        .close-sidebar {
            position: absolute;
            top: 20px;
            left: 20px;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--text-primary);
            cursor: pointer;
        }

        .mobile-nav-link {
            display: block;
            padding: 15px;
            text-decoration: none;
            color: var(--text-secondary);
            border-radius: 8px;
            margin-bottom: 5px;
            transition: var(--transition);
        }

        .mobile-nav-link:hover,
        .mobile-nav-link.active {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
        }

        /* قسم البطل */
        .hero {
            padding: 80px 0;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            align-items: center;
        }

        @media (max-width: 992px) {
            .hero {
                grid-template-columns: 1fr;
                text-align: center;
            }
        }

        .hero-content h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        @media (max-width: 768px) {
            .hero-content h1 {
                font-size: 2.2rem;
            }
        }

        .hero-content p {
            font-size: 1.2rem;
            color: var(--text-secondary);
            margin-bottom: 30px;
        }

        .hero-search {
            display: flex;
            gap: 10px;
            margin-bottom: 40px;
        }

        @media (max-width: 480px) {
            .hero-search {
                flex-direction: column;
            }
        }

        .hero-search input {
            flex: 1;
            padding: 15px 20px;
            border: 2px solid var(--border-color);
            border-radius: 10px;
            font-size: 1rem;
            background-color: var(--card-bg);
            color: var(--text-primary);
            transition: var(--transition);
        }

        .hero-search input:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
        }

        .btn-search {
            background-color: var(--primary-color);
            color: white;
            border: none;
            padding: 0 30px;
            border-radius: 10px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: var(--transition);
        }

        .btn-search:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .hero-stats {
            display: flex;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .hero-stats {
                flex-direction: column;
                gap: 20px;
            }
        }

        .stat {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .stat i {
            font-size: 2rem;
            color: var(--primary-color);
        }

        .stat-number {
            display: block;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-primary);
        }

        .stat-label {
            display: block;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .hero-image img {
            width: 100%;
            border-radius: 20px;
            box-shadow: var(--shadow-hover);
        }

        /* قسم المميزات */
        .features {
            padding: 80px 0;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            margin-bottom: 50px;
            color: var(--text-primary);
        }

        @media (max-width: 768px) {
            .section-title {
                font-size: 2rem;
            }
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        @media (max-width: 768px) {
            .features-grid {
                grid-template-columns: 1fr;
            }
        }

        .feature-card {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            text-align: center;
            transition: var(--transition);
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .feature-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 20px;
        }

        .feature-icon i {
            font-size: 2rem;
            color: white;
        }

        .feature-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
            color: var(--text-primary);
        }

        .feature-card p {
            color: var(--text-secondary);
            line-height: 1.8;
        }

        /* قسم النماذج */
        .recent-exams {
            padding: 80px 0;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }

        .view-all {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 5px;
            transition: var(--transition);
        }

        .view-all:hover {
            gap: 10px;
        }

        .exams-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 25px;
        }

        @media (max-width: 768px) {
            .exams-grid {
                grid-template-columns: 1fr;
            }
        }

        .exam-card {
            background-color: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
        }

        .exam-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
        }

        .exam-header {
            display: flex;
            justify-content: space-between;
            padding: 20px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
        }

        .difficulty-badge {
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 600;
            color: white;
        }

        .difficulty-badge.easy {
            background-color: var(--success-color);
        }

        .difficulty-badge.medium {
            background-color: var(--warning-color);
        }

        .difficulty-badge.hard {
            background-color: var(--danger-color);
        }

        .year-badge {
            background-color: white;
            color: var(--primary-color);
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 600;
        }

        .exam-body {
            padding: 20px;
        }

        .exam-body h3 {
            margin-bottom: 15px;
            color: var(--text-primary);
        }

        .exam-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .progress-stats {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 20px;
        }

        .avg-score {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
            padding: 5px 10px;
            border-radius: 8px;
            font-size: 0.9rem;
        }

        .stars {
            color: #ffc107;
        }

        .exam-footer {
            padding: 20px;
            border-top: 1px solid var(--border-color);
            display: flex;
            gap: 10px;
        }

        @media (max-width: 480px) {
            .exam-footer {
                flex-direction: column;
            }
        }

        .btn-preview, .btn-start {
            flex: 1;
            padding: 12px;
            border-radius: 8px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            transition: var(--transition);
        }

        .btn-preview {
            background-color: transparent;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
        }

        .btn-preview:hover {
            background-color: rgba(67, 97, 238, 0.1);
        }

        .btn-start {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-start:hover {
            background-color: var(--primary-dark);
        }

        /* قسم الإحصائيات الحية */
        .live-stats {
            padding: 80px 0;
        }

        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 25px;
        }

        @media (max-width: 768px) {
            .stats-container {
                grid-template-columns: 1fr;
            }
        }

        .stat-card {
            background-color: var(--card-bg);
            padding: 25px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: var(--transition);
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-hover);
        }

        .stat-trend {
            font-size: 0.8rem;
            padding: 3px 8px;
            border-radius: 12px;
            font-weight: 600;
        }

        .stat-trend.up {
            background-color: rgba(46, 204, 113, 0.2);
            color: var(--success-color);
        }

        .stat-trend.down {
            background-color: rgba(231, 76, 60, 0.2);
            color: var(--danger-color);
        }

        .stat-content {
            text-align: center;
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--text-primary);
            margin-bottom: 5px;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .stat-icon {
            font-size: 2rem;
            color: var(--primary-color);
        }

        /* التذييل */
        .footer {
            background-color: var(--card-bg);
            margin-top: 80px;
            border-top: 1px solid var(--border-color);
        }

        .footer-content {
            padding: 50px 0;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
        }

        .footer-section h3,
        .footer-section h4 {
            color: var(--text-primary);
            margin-bottom: 20px;
        }

        .footer-section p,
        .footer-section a {
            color: var(--text-secondary);
            margin-bottom: 10px;
            display: block;
            text-decoration: none;
            transition: var(--transition);
        }

        .footer-section a:hover {
            color: var(--primary-color);
            padding-right: 5px;
        }

        .social-icons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-icons a {
            width: 40px;
            height: 40px;
            background-color: rgba(67, 97, 238, 0.1);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary-color);
            font-size: 1.2rem;
            transition: var(--transition);
        }

        .social-icons a:hover {
            background-color: var(--primary-color);
            color: white;
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            padding: 20px;
            border-top: 1px solid var(--border-color);
            color: var(--text-secondary);
        }

        /* الإشعارات */
        .notification {
            position: fixed;
            bottom: 20px;
            left: 20px;
            background-color: var(--success-color);
            color: white;
            padding: 15px 20px;
            border-radius: 10px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 15px;
            z-index: 1002;
            transform: translateX(-150%);
            transition: transform 0.3s ease;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification-content {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .notification-close {
            background: none;
            border: none;
            color: white;
            cursor: pointer;
            font-size: 1.2rem;
        }

        /* لوحة التحكم */
        .dashboard-container {
            display: grid;
            grid-template-columns: 280px 1fr;
            min-height: calc(100vh - 70px);
        }

        @media (max-width: 992px) {
            .dashboard-container {
                grid-template-columns: 1fr;
            }
        }

        .sidebar {
            background-color: var(--card-bg);
            border-left: 1px solid var(--border-color);
            padding: 20px;
            position: sticky;
            top: 70px;
            height: calc(100vh - 70px);
            overflow-y: auto;
        }

        @media (max-width: 992px) {
            .sidebar {
                position: fixed;
                top: 70px;
                right: -280px;
                width: 280px;
                height: calc(100vh - 70px);
                z-index: 999;
                transition: right 0.3s ease;
            }
            
            .sidebar.active {
                right: 0;
            }
        }

        .user-info {
            text-align: center;
            padding: 20px 0;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 20px;
        }

        .user-avatar {
            width: 80px;
            height: 80px;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 15px;
        }

        .user-avatar i {
            font-size: 3rem;
            color: white;
        }

        .user-details h3 {
            margin-bottom: 5px;
            color: var(--text-primary);
        }

        .user-details p {
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .sidebar-menu {
            display: flex;
            flex-direction: column;
            gap: 5px;
            margin-bottom: 30px;
        }

        .menu-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 12px 15px;
            text-decoration: none;
            color: var(--text-secondary);
            border-radius: 8px;
            transition: var(--transition);
            position: relative;
        }

        .menu-item:hover,
        .menu-item.active {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
        }

        .badge {
            background-color: var(--primary-color);
            color: white;
            padding: 2px 8px;
            border-radius: 10px;
            font-size: 0.75rem;
            margin-right: auto;
        }

        .badge-danger {
            background-color: var(--danger-color);
        }

        .sidebar-footer {
            margin-top: auto;
            padding-top: 20px;
            border-top: 1px solid var(--border-color);
        }

        .progress-container {
            margin-bottom: 20px;
        }

        .progress-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
        }

        .progress-bar {
            height: 8px;
            background-color: var(--border-color);
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            border-radius: 4px;
        }

        .btn-upgrade {
            width: 100%;
            padding: 12px;
            background: linear-gradient(45deg, #ff9a00, #ff6a00);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            transition: var(--transition);
        }

        .btn-upgrade:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(255, 106, 0, 0.3);
        }

        .main-content {
            padding: 30px;
            overflow-y: auto;
            max-height: calc(100vh - 70px);
        }

        @media (max-width: 768px) {
            .main-content {
                padding: 20px;
            }
        }

        .welcome-section {
            margin-bottom: 30px;
        }

        .welcome-section h1 {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--text-primary);
        }

        .welcome-section p {
            color: var(--text-secondary);
            margin-bottom: 20px;
        }

        .quick-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        @media (max-width: 768px) {
            .quick-stats {
                grid-template-columns: 1fr;
            }
        }

        .quick-stat {
            background-color: var(--card-bg);
            padding: 20px;
            border-radius: 12px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 15px;
            transition: var(--transition);
        }

        .quick-stat:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-hover);
        }

        .quick-stat i {
            font-size: 2rem;
            color: var(--primary-color);
        }

        .quick-stat .number {
            display: block;
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--text-primary);
        }

        .quick-stat .label {
            display: block;
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        .card {
            background-color: var(--card-bg);
            padding: 25px;
            border-radius: 15px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }

        .continue-exam {
            margin-bottom: 30px;
        }

        .exam-continue {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(45deg, rgba(67, 97, 238, 0.1), rgba(114, 9, 183, 0.1));
            padding: 25px;
            border-radius: 12px;
            margin-top: 20px;
        }

        @media (max-width: 768px) {
            .exam-continue {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }
        }

        .exam-info h3 {
            margin-bottom: 10px;
            color: var(--text-primary);
        }

        .exam-info p {
            color: var(--text-secondary);
            margin-bottom: 15px;
        }

        .exam-progress {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        @media (max-width: 768px) {
            .exam-progress {
                flex-direction: column;
                gap: 10px;
            }
        }

        .btn-continue {
            background: linear-gradient(45deg, var(--primary-color), var(--secondary-color));
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: var(--transition);
        }

        .btn-continue:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(67, 97, 238, 0.3);
        }

        .quick-insights {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        @media (max-width: 768px) {
            .quick-insights {
                grid-template-columns: 1fr;
            }
        }

        .study-time {
            display: flex;
            justify-content: space-around;
            margin: 30px 0;
        }

        .time-stat {
            text-align: center;
        }

        .time-value {
            display: block;
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary-color);
            line-height: 1;
        }

        .time-label {
            display: block;
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-top: 5px;
        }

        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 5px;
        }

        .calendar-day {
            aspect-ratio: 1;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 5px;
            font-size: 0.9rem;
            font-weight: 600;
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
        }

        .recommended-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        @media (max-width: 768px) {
            .recommended-grid {
                grid-template-columns: 1fr;
            }
        }

        .recommended-exam {
            background-color: rgba(67, 97, 238, 0.05);
            padding: 20px;
            border-radius: 12px;
            border: 2px solid transparent;
            transition: var(--transition);
            cursor: pointer;
        }

        .recommended-exam:hover {
            border-color: var(--primary-color);
            transform: translateY(-3px);
        }

        .recommended-exam h4 {
            margin-bottom: 10px;
            color: var(--text-primary);
        }

        .recommended-exam p {
            color: var(--text-secondary);
            font-size: 0.9rem;
            margin-bottom: 15px;
        }

        .recommended-exam .exam-meta {
            display: flex;
            justify-content: space-between;
            color: var(--text-secondary);
            font-size: 0.85rem;
        }

        .table-container {
            overflow-x: auto;
            margin-top: 20px;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        thead {
            background-color: rgba(67, 97, 238, 0.1);
        }

        th {
            padding: 15px;
            text-align: right;
            color: var(--text-primary);
            font-weight: 600;
            border-bottom: 2px solid var(--border-color);
        }

        td {
            padding: 15px;
            border-bottom: 1px solid var(--border-color);
            color: var(--text-secondary);
        }

        tr:hover {
            background-color: rgba(67, 97, 238, 0.05);
        }

        .score-cell {
            font-weight: 600;
        }

        .score-cell.high {
            color: var(--success-color);
        }

        .score-cell.medium {
            color: var(--warning-color);
        }

        .score-cell.low {
            color: var(--danger-color);
        }

        .action-buttons {
            display: flex;
            gap: 8px;
        }

        .btn-action {
            padding: 6px 12px;
            border-radius: 6px;
            border: none;
            font-size: 0.85rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .btn-view {
            background-color: rgba(52, 152, 219, 0.1);
            color: var(--info-color);
        }

        .btn-retry {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
        }

        .btn-action:hover {
            opacity: 0.8;
        }

        /* زر المستخدم */
        .user-dropdown {
            position: relative;
        }

        .user-btn {
            display: flex;
            align-items: center;
            gap: 10px;
            background: none;
            border: none;
            color: var(--text-primary);
            font-size: 1rem;
            cursor: pointer;
            padding: 8px 15px;
            border-radius: 8px;
            transition: var(--transition);
        }

        .user-btn:hover {
            background-color: rgba(0, 0, 0, 0.05);
        }

        .user-btn i:first-child {
            font-size: 1.5rem;
        }

        @media (max-width: 768px) {
            .user-btn span {
                display: none;
            }
        }

        .dropdown-menu {
            position: absolute;
            top: 100%;
            left: 0;
            background-color: var(--card-bg);
            box-shadow: var(--shadow-hover);
            border-radius: 8px;
            padding: 10px 0;
            min-width: 200px;
            display: none;
            z-index: 100;
        }

        .user-dropdown:hover .dropdown-menu {
            display: block;
        }

        .dropdown-menu a {
            display: flex;
            align-items: center;
            gap: 10px;
            padding: 10px 20px;
            text-decoration: none;
            color: var(--text-secondary);
            transition: var(--transition);
        }

        .dropdown-menu a:hover {
            background-color: rgba(67, 97, 238, 0.1);
            color: var(--primary-color);
        }

        .dropdown-menu hr {
            border: none;
            height: 1px;
            background-color: var(--border-color);
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <!-- شريط التنقل -->
    <nav class="navbar">
        <div class="container nav-container">
            <div class="nav-brand">
                <i class="fas fa-graduation-cap"></i>
                <span>نظام الاختبارات</span>
            </div>
            
            <div class="nav-menu">
                <a href="#home" class="nav-link active"><i class="fas fa-home"></i> الرئيسية</a>
                <a href="#features" class="nav-link"><i class="fas fa-star"></i> المميزات</a>
                <a href="#exams" class="nav-link"><i class="fas fa-book"></i> النماذج</a>
                <a href="#stats" class="nav-link"><i class="fas fa-chart-bar"></i> الإحصائيات</a>
                <a href="#dashboard" class="nav-link"><i class="fas fa-tachometer-alt"></i> لوحة التحكم</a>
            </div>
            
            <div class="nav-actions">
                <button class="btn-theme" id="themeToggle">
                    <i class="fas fa-moon"></i>
                </button>
                <div class="user-dropdown">
                    <button class="user-btn">
                        <i class="fas fa-user-circle"></i>
                        <span>محمد أحمد</span>
                        <i class="fas fa-chevron-down"></i>
                    </button>
                    <div class="dropdown-menu">
                        <a href="#profile"><i class="fas fa-user"></i> الملف الشخصي</a>
                        <a href="#settings"><i class="fas fa-cog"></i> الإعدادات</a>
                        <a href="#help"><i class="fas fa-question-circle"></i> المساعدة</a>
                        <hr>
                        <a href="#logout"><i class="fas fa-sign-out-alt"></i> تسجيل الخروج</a>
                    </div>
                </div>
                <button class="btn-mobile-menu" id="mobileMenuBtn">
                    <i class="fas fa-bars"></i>
                </button>
            </div>
        </div>
    </nav>

    <!-- القائمة الجانبية للجوال -->
    <div class="mobile-sidebar" id="mobileSidebar">
        <button class="close-sidebar" id="closeSidebar">
            <i class="fas fa-times"></i>
        </button>
        <a href="#home" class="mobile-nav-link active">
            <i class="fas fa-home"></i> الرئيسية
        </a>
        <a href="#features" class="mobile-nav-link">
            <i class="fas fa-star"></i> المميزات
        </a>
        <a href="#exams" class="mobile-nav-link">
            <i class="fas fa-book"></i> النماذج
        </a>
        <a href="#stats" class="mobile-nav-link">
            <i class="fas fa-chart-bar"></i> الإحصائيات
        </a>
        <a href="#dashboard" class="mobile-nav-link">
            <i class="fas fa-tachometer-alt"></i> لوحة التحكم
        </a>
        <hr>
        <a href="#login" class="mobile-nav-link">
            <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
        </a>
    </div>

    <!-- الصفحة الرئيسية -->
    <div id="home">
        <!-- قسم البطل -->
        <section class="hero">
            <div class="container">
                <div class="hero-content">
                    <h1>حل نماذج الاختبارات السابقة بذكاء</h1>
                    <p>أكثر من 5000 نموذج اختبار سابق من مختلف الكليات والمستويات</p>
                    <div class="hero-search">
                        <input type="text" placeholder="ابحث عن نموذج اختبار..." id="searchInput">
                        <button class="btn-search" onclick="performSearch()">
                            <i class="fas fa-search"></i> بحث
                        </button>
                    </div>
                    <div class="hero-stats">
                        <div class="stat">
                            <i class="fas fa-users"></i>
                            <div>
                                <span class="stat-number">5,247</span>
                                <span class="stat-label">طالب مسجل</span>
                            </div>
                        </div>
                        <div class="stat">
                            <i class="fas fa-file-alt"></i>
                            <div>
                                <span class="stat-number">1,856</span>
                                <span class="stat-label">نموذج اختبار</span>
                            </div>
                        </div>
                        <div class="stat">
                            <i class="fas fa-university"></i>
                            <div>
                                <span class="stat-number">24</span>
                                <span class="stat-label">كلية</span>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="hero-image">
                    <div style="width: 100%; height: 400px; background: linear-gradient(45deg, #4361ee, #7209b7); border-radius: 20px; display: flex; align-items: center; justify-content: center; color: white; font-size: 2rem;">
                        <i class="fas fa-graduation-cap" style="font-size: 8rem; opacity: 0.7;"></i>
                    </div>
                </div>
            </div>
        </section>

        <!-- قسم المميزات -->
        <section class="features" id="features">
            <div class="container">
                <h2 class="section-title">مميزات النظام</h2>
                <div class="features-grid">
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-brain"></i>
                        </div>
                        <h3>معالجة ذكية</h3>
                        <p>تحويل تلقائي لصور الاختبارات إلى أسئلة تفاعلية باستخدام الذكاء الاصطناعي</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-chart-line"></i>
                        </div>
                        <h3>تتبع التقدم</h3>
                        <p>تحليلات مفصلة لتطور مستواك ونقاط القوة والضعف في كل مادة</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-bolt"></i>
                        </div>
                        <h3>نتائج فورية</h3>
                        <p>تصحيح آلي فوري مع شرح للإجابات فور إنهاء الاختبار</p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-mobile-alt"></i>
                        </div>
                        <h3>متوافق مع الجوال</h3>
                        <p>تصميم متجاوب يعمل على جميع الأجهزة بشكل سلس</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- قسم أحدث النماذج -->
        <section class="recent-exams" id="exams">
            <div class="container">
                <div class="section-header">
                    <h2 class="section-title">أحدث النماذج المضافة</h2>
                    <a href="#" class="view-all">عرض الكل <i class="fas fa-arrow-left"></i></a>
                </div>
                
                <div class="exams-grid" id="examsGrid">
                    <!-- سيتم إضافة النماذج ديناميكياً -->
                </div>
            </div>
        </section>

        <!-- قسم إحصائيات حية -->
        <section class="live-stats" id="stats">
            <div class="container">
                <h2 class="section-title">إحصائيات حية</h2>
                <div class="stats-container">
                    <div class="stat-card">
                        <div class="stat-trend up">
                            <i class="fas fa-arrow-up"></i> 12%
                        </div>
                        <div class="stat-content">
                            <div class="stat-value" id="liveExams">0</div>
                            <div class="stat-label">اختبار يتم حلها الآن</div>
                        </div>
                        <div class="stat-icon">
                            <i class="fas fa-clock"></i>
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <div class="stat-trend up">
                            <i class="fas fa-arrow-up"></i> 8%
                        </div>
                        <div class="stat-content">
                            <div class="stat-value" id="todayTests">0</div>
                            <div class="stat-label">اختبار اليوم</div>
                        </div>
                        <div class="stat-icon">
                            <i class="fas fa-calendar-day"></i>
                        </div>
                    </div>
                    
                    <div class="stat-card">
                        <div class="stat-trend down">
                            <i class="fas fa-arrow-down"></i> 3%
                        </div>
                        <div class="stat-content">
                            <div class="stat-value" id="avgScore">0%</div>
                            <div class="stat-label">متوسط النتائج</div>
                        </div>
                        <div class="stat-icon">
                            <i class="fas fa-chart-pie"></i>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>

    <!-- لوحة التحكم -->
    <div id="dashboard" style="display: none;">
        <div class="dashboard-container">
            <!-- الشريط الجانبي -->
            <aside class="sidebar">
                <div class="user-info">
                    <div class="user-avatar">
                        <i class="fas fa-user-circle"></i>
                    </div>
                    <div class="user-details">
                        <h3>محمد أحمد</h3>
                        <p>طالب - كلية الهندسة</p>
                    </div>
                </div>
                
                <div class="sidebar-menu">
                    <a href="#dashboard-overview" class="menu-item active">
                        <i class="fas fa-home"></i>
                        <span>نظرة عامة</span>
                    </a>
                    <a href="#my-exams" class="menu-item">
                        <i class="fas fa-book-open"></i>
                        <span>نماذجي</span>
                        <span class="badge">12</span>
                    </a>
                    <a href="#assignments" class="menu-item">
                        <i class="fas fa-tasks"></i>
                        <span>الواجبات</span>
                        <span class="badge badge-danger">3</span>
                    </a>
                    <a href="#progress" class="menu-item">
                        <i class="fas fa-chart-line"></i>
                        <span>التقدم الدراسي</span>
                    </a>
                    <a href="#achievements" class="menu-item">
                        <i class="fas fa-medal"></i>
                        <span>الإنجازات</span>
                    </a>
                    <a href="#calendar" class="menu-item">
                        <i class="fas fa-calendar-alt"></i>
                        <span>الجدول الزمني</span>
                    </a>
                    <a href="#files" class="menu-item">
                        <i class="fas fa-file-download"></i>
                        <span>الملفات</span>
                    </a>
                    <a href="#settings" class="menu-item">
                        <i class="fas fa-cog"></i>
                        <span>الإعدادات</span>
                    </a>
                </div>
                
                <div class="sidebar-footer">
                    <div class="progress-container">
                        <div class="progress-info">
                            <span>التقدم العام</span>
                            <span>65%</span>
                        </div>
                        <div class="progress-bar">
                            <div class="progress-fill" style="width: 65%"></div>
                        </div>
                    </div>
                    <button class="btn-upgrade">
                        <i class="fas fa-crown"></i>
                        ترقية الحساب
                    </button>
                </div>
            </aside>

            <!-- المحتوى الرئيسي -->
            <main class="main-content">
                <!-- قسم الترحيب -->
                <div class="welcome-section">
                    <h1>مرحباً بعودتك، محمد! 👋</h1>
                    <p>لديك 3 اختبارات قادمة هذا الأسبوع</p>
                    <div class="quick-stats">
                        <div class="quick-stat">
                            <i class="fas fa-check-circle"></i>
                            <div>
                                <span class="number">12</span>
                                <span class="label">نموذج محلول</span>
                            </div>
                        </div>
                        <div class="quick-stat">
                            <i class="fas fa-clock"></i>
                            <div>
                                <span class="number">85%</span>
                                <span class="label">متوسط النتائج</span>
                            </div>
                        </div>
                        <div class="quick-stat">
                            <i class="fas fa-fire"></i>
                            <div>
                                <span class="number">7</span>
                                <span class="label">أيام متتالية</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- إكمال الاختبار -->
                <div class="continue-exam card">
                    <h2><i class="fas fa-play-circle"></i> استمر حيث توقفت</h2>
                    <div class="exam-continue">
                        <div class="exam-info">
                            <h3>رياضيات 2023 - الاختبار النهائي</h3>
                            <p>السؤال 15 من 30 | متبقي: 45:00 دقيقة</p>
                            <div class="exam-progress">
                                <div class="progress-bar">
                                    <div class="progress-fill" style="width: 50%"></div>
                                </div>
                                <span>50% مكتمل</span>
                            </div>
                        </div>
                        <button class="btn-continue" onclick="continueExam()">
                            <i class="fas fa-play"></i> استكمال الاختبار
                        </button>
                    </div>
                </div>

                <!-- إحصائيات سريعة -->
                <div class="quick-insights">
                    <div class="insight-card card">
                        <h3><i class="fas fa-chart-pie"></i> توزيع النتائج</h3>
                        <canvas id="scoreDistribution"></canvas>
                    </div>
                    
                    <div class="insight-card card">
                        <h3><i class="fas fa-trend-up"></i> تقدم المستوى</h3>
                        <canvas id="progressChart"></canvas>
                    </div>
                    
                    <div class="insight-card card">
                        <h3><i class="fas fa-clock"></i> وقت الدراسة</h3>
                        <div class="study-time">
                            <div class="time-stat">
                                <span class="time-value">12.5</span>
                                <span class="time-label">ساعة هذا الأسبوع</span>
                            </div>
                            <div class="time-stat">
                                <span class="time-value">2.1</span>
                                <span class="time-label">ساعة/يوم</span>
                            </div>
                        </div>
                        <div class="calendar-grid" id="calendarGrid">
                            <!-- سيتم إضافة أيام الأسبوع -->
                        </div>
                    </div>
                </div>

                <!-- النماذج المقترحة -->
                <div class="recommended-exams card">
                    <div class="section-header">
                        <h2><i class="fas fa-lightbulb"></i> مقترحة لك</h2>
                        <a href="#" class="view-all">عرض الكل <i class="fas fa-arrow-left"></i></a>
                    </div>
                    
                    <div class="recommended-grid" id="recommendedGrid">
                        <!-- سيتم إضافة النماذج ديناميكياً -->
                    </div>
                </div>

                <!-- جدول الاختبارات الأخيرة -->
                <div class="recent-tests card
