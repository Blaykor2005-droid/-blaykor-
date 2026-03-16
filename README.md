# -blaykor-
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Blaykor Pro - محرك نمو إنستغرام</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Cairo', sans-serif;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            min-height: 100vh;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header */
        .header {
            text-align: center;
            margin-bottom: 40px;
            color: white;
            position: relative;
        }

        .logo {
            font-size: 3.5rem;
            font-weight: 700;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1, #feca57);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 15px;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @keyframes glow {
            from { filter: drop-shadow(0 0 5px #ff6b6b); }
            to { filter: drop-shadow(0 0 20px #4ecdc4); }
        }

        /* Navigation Tabs */
        .nav-tabs {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .tab-btn {
            padding: 12px 25px;
            background: rgba(255,255,255,0.1);
            border: none;
            border-radius: 25px;
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .tab-btn.active {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            transform: scale(1.05);
        }

        /* Content Sections */
        .section {
            display: none;
            animation: fadeIn 0.5s ease-in;
        }

        .section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Cards */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.15);
            backdrop-filter: blur(15px);
            transition: all 0.4s ease;
            border: 1px solid rgba(255,255,255,0.3);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, #ff6b6b, #4ecdc4, #45b7d1);
        }

        .card:hover {
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 30px 80px rgba(0,0,0,0.25);
        }

        .card h3 {
            color: #2a5298;
            margin-bottom: 20px;
            font-size: 1.6rem;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        /* Profile Analyzer */
        .profile-input {
            width: 100%;
            padding: 15px;
            border: 2px solid #e1e5e9;
            border-radius: 12px;
            font-size: 1rem;
            margin-bottom: 20px;
            font-family: inherit;
            transition: border-color 0.3s ease;
        }

        .profile-input:focus {
            outline: none;
            border-color: #4ecdc4;
        }

        .profile-score {
            font-size: 3rem;
            font-weight: 700;
            margin: 20px 0;
        }

        .score-excellent { color: #4ecdc4; }
        .score-good { color: #feca57; }
        .score-needs-work { color: #ff6b6b; }

        /* Competitor Spy */
        .competitor-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }

        .competitor-card {
            border: 2px solid #e1e5e9;
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .competitor-card:hover {
            border-color: #4ecdc4;
            transform: translateY(-5px);
        }

        /* Scheduler */
        .scheduler-item {
            background: #f8f9ff;
            padding: 20px;
            margin-bottom: 15px;
            border-radius: 12px;
            border-right: 4px solid #667eea;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .scheduler-controls {
            display: flex;
            gap: 10px;
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
            font-family: inherit;
        }

        .btn-primary {
            background: linear-gradient(45deg, #4ecdc4, #44bdad);
            color: white;
        }

        .btn-success {
            background: linear-gradient(45deg, #4facfe, #00f2fe);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        /* Analytics Charts */
        .chart-container {
            height: 300px;
            background: #f8f9ff;
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
            position: relative;
            overflow: hidden;
        }

        .fake-chart {
            height: 100%;
            display: flex;
            align-items: flex-end;
            gap: 5px;
            padding: 20px 0;
        }

        .chart-bar {
            flex: 1;
            background: linear-gradient(45deg, #4ecdc4, #44bdad);
            border-radius: 5px 5px 0 0;
            animation: grow 2s ease-out;
            position: relative;
        }

        .chart-bar:nth-child(2) { background: linear-gradient(45deg, #feca57, #ff9ff3); animation-delay: 0.2s; }
        .chart-bar:nth-child(3) { background: linear-gradient(45deg, #ff6b6b, #ee5a24); animation-delay: 0.4s; }
        .chart-bar:nth-child(4) { background: linear-gradient(45deg, #54a0ff, #2e86de); animation-delay: 0.6s; }

        @keyframes grow {
            from { height: 0; }
            to { height: var(--height); }
        }

        /* Floating Elements */
        .floating-notification {
            position: fixed;
            top: 100px;
            right: 20px;
            background: linear-gradient(45deg, #4ecdc4, #44bdad);
            color: white;
            padding: 20px 30px;
            border-radius: 15px;
            box-shadow: 0 20px 40px rgba(78,205,196,0.3);
            transform: translateX(400px);
            transition: transform 0.4s ease;
            z-index: 10000;
            font-weight: 600;
        }

        .floating-notification.show {
            transform: translateX(0);
        }

        .floating-action {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 70px;
            height: 70px;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            border: none;
            border-radius: 50%;
            color: white;
            font-size: 1.8rem;
            cursor: pointer;
            box-shadow: 0 15px 40px rgba(255,107,107,0.4);
            transition: all 0.3s ease;
            z-index: 1000;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr;
            }
            .nav-tabs {
                flex-direction: column;
                align-items: center;
            }
            .logo {
                font-size: 2.5rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <h1 class="logo">Blaykor Pro</h1>
            <p style="font-size: 1.3rem; opacity: 0.9;">🔥 أقوى أداة لنمو الإنستغرام - كل الميزات المتقدمة</p>
        </div>

        <!-- Navigation -->
        <div class="nav-tabs">
            <button class="tab-btn active" onclick="showSection('dashboard')">
                <i class="fas fa-tachometer-alt"></i> لوحة التحكم
            </button>
            <button class="tab-btn" onclick="showSection('analyzer')">
                <i class="fas fa-user-analyzer"></i> تحليل الملف
            </button>
            <button class="tab-btn" onclick="showSection('competitors')">
                <i class="fas fa-eye"></i> جاسوس المنافسين
            </button>
            <button class="tab-btn" onclick="showSection('scheduler')">
                <i class="fas fa-calendar-alt"></i> المجدول
            </button>
            <button class="tab-btn" onclick="showSection('analytics')">
                <i class="fas fa-chart-bar"></i> التحليلات
            </button>
        </div>

        <!-- Dashboard Section -->
        <div id="dashboard" class="section active">
            <div class="dashboard-grid">
                <div class="card">
                    <h3><i class="fas fa-chart-line"></i> إحصائيات النمو</h3>
                    <div style="font-size: 3rem; font-weight: 700; color: #4ecdc4; margin: 20px 0;">+2,847</div>
                    <p style="font-size: 1.2rem; color: #666;">متابع جديد هذا الأسبوع</p>
                    <div style="display: flex; gap: 20px; margin-top: 30px;">
                        <div style="flex: 1; text-align: center;">
                            <div style="font-size: 2rem; color: #feca57;">12.4%</div>
                            <small>نمو المتابعين</small>
                        </div>
                        <div style="flex: 1; text-align: center;">
                            <div style="font-size: 2rem; color: #ff6b6b;">8.2%</div>
                            <small>معدل التفاعل</div>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <h3><i class="fas fa-rocket"></i> خطة اليوم</h3>
                    <div class="scheduler-item">
                        <span>📱 نشر 3 ستوري</span>
                        <div class="scheduler-controls">
                            <button class="btn btn-success btn-sm" onclick="completeTask(this)">✅</button>
                        </div>
                    </div>
                    <div class="scheduler-item">
                        <span>💬 تفاعل مع 100 حساب</span>
                        <div class="scheduler-controls">
                            <button class="btn btn-success btn-sm" onclick="completeTask(this)">✅</button>
                        </div>
                    </div>
                    <button class="btn btn-primary" style="width: 100%; margin-top: 20px;" onclick="showNotification('تم حفظ خطة اليوم! 🎉')">
                        حفظ التقدم
                    </button>
                </div>

                <div class="card">
                    <h3><i class="fas fa-magic"></i> مولد الهاشتاج</h3>
                    <div style="display: flex; gap: 15px; margin-bottom: 20px; flex-wrap: wrap;">
                        <input class="profile-input" id="proNiche" placeholder="مجالك (رياضة، أزياء، طعام)" value="رياضة">
                        <button class="btn btn-primary" onclick="generateProHashtags()">توليد هاشتاج</button>
                    </div>
                    <div id="proHashtags" style="display: flex; flex-wrap: wrap; gap: 8px;"></div>
                </div>
            </div>
        </div>

        <!-- Profile Analyzer -->
        <div id="analyzer" class="section">
            <div class="dashboard-grid">
                <div class="card" style="grid-column: 1 / -1;">
                    <h3><i class="fas fa-user-analyzer"></i> تحليل الملف الشخصي</h3>
                    <input class="profile-input" id="profileUrl" placeholder="https://instagram.com/yourusername" value="https://instagram.com/fitnesspro">
                    <button class="btn btn-primary" style="width: 200px; margin: 20px auto; display: block;" onclick="analyzeProfile()">تحليل الآن</button>
                    
                    <div id="profileResults" style="margin-top: 30px;">
                        <div class="profile-score score-excellent" id="profileScore">85/100</div>
                        <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 20px; margin-top: 30px;">
                            <div>
                                <div style="font-size: 1.5rem; font-weight: 700; color: #4ecdc4;">البيو</div>
                                <div style="color: #666;">ممتاز ✅</div>
                            </div>
                            <div>
                                <div style="font-size: 1.5rem; font-weight: 700; color: #feca57;">الصورة</div>
                                <div style="color: #666;">جيد 👍</div>
                            </div>
                            <div>
                                <div style="font-size: 1.5rem; font-weight: 700; color: #ff6b6b;">الهاشتاج</div>
                                <div style="color: #666;">يحتاج تحسين ⚠️</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Competitor Spy -->
        <div id="competitors" class="section">
            <div class="dashboard-grid">
                <div class="card">
                    <h3><i class="fas fa-eye"></i> جاسوس المنافسين</h3>
                    <input class="profile-input" id="competitorUrl" placeholder="أدخل حساب المنافس">
                    <button class="btn btn-primary" onclick="spyCompetitor()" style="width: 100%; margin-top: 20px;">التجسس</button>
                    
                    <div id="competitorResults" style="margin-top: 30px;">
                        <div class="competitor-grid">
                            <div class="competitor-card">
                                <i class="fas fa-users" style="font-size: 2rem; color: #4ecdc4;"></i>
                                <div style="font-size: 1.5rem; font-weight: 700;">156K</div>
                                <small>المتابعين</small>
                            </div>
                            <div class="competitor-card">
                                <i class="fas fa-fire" style="font-size: 2rem; color: #feca57;"></i>
                                <div style="font-size: 1.5rem; font-weight: 700;">9.2%</div>
                                <small>معدل التفاعل</small>
                            </div>
                            <div class="competitor-card">
                                <i class="fas fa-calendar" style="font-size: 2rem; color: #ff6b6b;"></i>
                                <div style="font-size: 1.5rem; font-weight: 700;">يومياً</div>
                                <small>معدل النشر</small>
                            </div>
                        </div>
                        <div style="margin-top: 20px; padding: 20px; background: #f8f9
                        
