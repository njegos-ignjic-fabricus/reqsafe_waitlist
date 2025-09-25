<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ReqSafe - Guard Your Requirements. Control Every Release.</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #204482 0%, #3F83EA 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 0;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #204482;
            display: flex;
            align-items: center;
        }

        .logo::before {
            content: "🛡️";
            margin-right: 10px;
            font-size: 2rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: #3F83EA;
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, #204482 0%, #3F83EA 100%);
            color: white;
            padding: 120px 0 80px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
            opacity: 0.3;
        }

        .hero-content {
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-size: 3.5rem;
            font-weight: 700;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
            animation: fadeInUp 1s ease;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
            opacity: 0.95;
            animation: fadeInUp 1s ease 0.2s both;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(45deg, #46B763, #3F83EA);
            color: white;
            padding: 15px 40px;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            box-shadow: 0 8px 25px rgba(70, 183, 99, 0.3);
            animation: fadeInUp 1s ease 0.4s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 12px 35px rgba(70, 183, 99, 0.4);
            background: linear-gradient(45deg, #3F83EA, #46B763);
        }

        /* Problem Section */
        .problem {
            background: white;
            padding: 80px 0;
            position: relative;
        }

        .section-title {
            text-align: center;
            font-size: 2.5rem;
            color: #204482;
            margin-bottom: 3rem;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(45deg, #3F83EA, #46B763);
            border-radius: 2px;
        }

        .problem-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .problem-item {
            background: linear-gradient(135deg, #204482 0%, #3F83EA 100%);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            color: white;
            font-weight: 500;
            box-shadow: 0 10px 30px rgba(32, 68, 130, 0.3);
            transition: transform 0.3s ease;
        }

        .problem-item:hover {
            transform: translateY(-5px);
        }

        .problem-item::before {
            content: "⚠️";
            display: block;
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        /* Solution Section */
        .solution {
            background: linear-gradient(135deg, rgba(70, 183, 99, 0.1) 0%, rgba(63, 131, 234, 0.1) 100%);
            padding: 80px 0;
        }

        .solution-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .solution-item {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            border-left: 5px solid #46B763;
        }

        .solution-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
            border-left-color: #3F83EA;
        }

        .solution-item h3 {
            color: #204482;
            margin-bottom: 1rem;
            font-size: 1.3rem;
        }

        .solution-item h3::before {
            content: "✅";
            margin-right: 10px;
        }

        /* Workflow Section */
        .workflow {
            background: white;
            padding: 80px 0;
            text-align: center;
        }

        .workflow-diagram {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-wrap: wrap;
            gap: 2rem;
            margin: 3rem 0;
        }

        .workflow-step {
            background: linear-gradient(135deg, #204482 0%, #3F83EA 100%);
            color: white;
            padding: 1.5rem;
            border-radius: 15px;
            min-width: 150px;
            position: relative;
            box-shadow: 0 8px 25px rgba(32, 68, 130, 0.3);
            transition: all 0.3s ease;
        }

        .workflow-step:hover {
            background: linear-gradient(135deg, #46B763 0%, #3F83EA 100%);
            transform: translateY(-3px);
        }

        .workflow-step:not(:last-child)::after {
            content: "→";
            position: absolute;
            right: -30px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 2rem;
            color: #3F83EA;
        }

        /* Benefits Section */
        .benefits {
            background: linear-gradient(135deg, rgba(32, 68, 130, 0.05) 0%, rgba(70, 183, 99, 0.05) 100%);
            padding: 80px 0;
        }

        .benefits-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .benefit-item {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(32, 68, 130, 0.1);
            transition: all 0.3s ease;
            border-top: 4px solid #46B763;
        }

        .benefit-item:hover {
            transform: translateY(-5px);
            border-top-color: #3F83EA;
            box-shadow: 0 15px 40px rgba(32, 68, 130, 0.15);
        }

        .benefit-item h3 {
            color: #204482;
            margin-bottom: 1rem;
        }

        .benefit-item::before {
            content: "🎯";
            display: block;
            font-size: 2rem;
            margin-bottom: 1rem;
        }

        /* CTA Section */
        .final-cta {
            background: linear-gradient(135deg, #204482 0%, #3F83EA 100%);
            color: white;
            padding: 80px 0;
            text-align: center;
        }

        .final-cta h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        /* Footer */
        footer {
            background: #204482;
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        .footer-links {
            margin-top: 1rem;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            margin: 0 1rem;
            transition: color 0.3s ease;
        }

        .footer-links a:hover {
            color: #46B763;
        }

        /* Animations */
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

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .hero p {
                font-size: 1.1rem;
            }
            
            .nav-links {
                display: none;
            }
            
            .workflow-step:not(:last-child)::after {
                content: "↓";
                right: 50%;
                top: 100%;
                transform: translateX(50%);
            }
        }
    </style>
</head>
<body>
    <header>
        <nav class="container">
            <div class="logo">ReqSafe</div>
            <ul class="nav-links">
                <li><a href="#problem">Problem</a></li>
                <li><a href="#solution">Solution</a></li>
                <li><a href="#workflow">Workflow</a></li>
                <li><a href="#benefits">Benefits</a></li>
            </ul>
        </nav>
    </header>

    <section class="hero">
        <div class="container">
            <div class="hero-content">
                <h1>Guard Your Requirements. Control Every Release.</h1>
                <p>ReqSafe connects your requirements, QA, and pipelines — ensuring nothing ships without approval. Import existing data, integrate with tools you already use, and release with confidence.</p>
                <a href="#waitlist" class="cta-button">👉 Join the Early Access Waitlist</a>
            </div>
        </div>
    </section>

    <section id="problem" class="problem">
        <div class="container">
            <h2 class="section-title">The Problem</h2>
            <div class="problem-grid">
                <div class="problem-item">
                    Requirements scattered across Jira, Confluence, or spreadsheets.
                </div>
                <div class="problem-item">
                    QA tracked separately, often manual.
                </div>
                <div class="problem-item">
                    Pipelines release builds without proper sign-off.
                </div>
                <div class="problem-item">
                    Compliance reports take hours to prepare.
                </div>
            </div>
        </div>
    </section>

    <section id="solution" class="solution">
        <div class="container">
            <h2 class="section-title">The ReqSafe Solution</h2>
            <div class="solution-grid">
                <div class="solution-item">
                    <h3>Requirements + Test Scenarios in One Place</h3>
                    <p>Link every request with its test cases.</p>
                </div>
                <div class="solution-item">
                    <h3>In-App QA Test Sessions</h3>
                    <p>Run tests, mark Pass/Fail/Warning, and generate audit-ready reports.</p>
                </div>
                <div class="solution-item">
                    <h3>Automated Release Control</h3>
                    <p>ReqSafe gates your CI/CD pipeline. Only approved builds ship.</p>
                </div>
                <div class="solution-item">
                    <h3>Data Import from Competitors</h3>
                    <p>Migrate from ReqView, Confluence, and others with ease.</p>
                </div>
                <div class="solution-item">
                    <h3>Seamless Integrations</h3>
                    <p>Display your full Software Requirements Specification (SRS) directly in Confluence via plugins.</p>
                </div>
                <div class="solution-item">
                    <h3>Flexible Storage Options</h3>
                    <p>Use ReqSafe's encrypted servers, your cloud (Google Drive, OneDrive, Dropbox), or your Git repo.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="workflow" class="workflow">
        <div class="container">
            <h2 class="section-title">Workflow Snapshot</h2>
            <div class="workflow-diagram">
                <div class="workflow-step">Spec</div>
                <div class="workflow-step">Linked Tests</div>
                <div class="workflow-step">QA Session</div>
                <div class="workflow-step">Approval</div>
                <div class="workflow-step">Release (or Stop)</div>
            </div>
            <p style="font-style: italic; color: #666; margin-top: 2rem;">
                Requirements → Test execution → Pipeline gate → Release decision
            </p>
        </div>
    </section>

    <section id="benefits" class="benefits">
        <div class="container">
            <h2 class="section-title">Why Teams Choose ReqSafe</h2>
            <div class="benefits-grid">
                <div class="benefit-item">
                    <h3>Audit-ready releases</h3>
                    <p>ISO, FDA, SOX, GDPR compliance</p>
                </div>
                <div class="benefit-item">
                    <h3>Seamless Integration</h3>
                    <p>Works with GitHub/GitLab pipelines</p>
                </div>
                <div class="benefit-item">
                    <h3>No Lock-in</h3>
                    <p>Import existing data, keep Confluence in the loop</p>
                </div>
                <div class="benefit-item">
                    <h3>Industry-Ready</h3>
                    <p>Designed for regulated industries (finance, healthcare, automotive, aerospace, gov)</p>
                </div>
            </div>
        </div>
    </section>

    <section id="waitlist" class="final-cta">
        <div class="container">
            <h2>Be among the first to safeguard your releases.</h2>
            <a href="#" class="cta-button">👉 Join the Early Access Waitlist</a>
        </div>
    </section>

    <footer>
        <div class="container">
            <p>ReqSafe © 2025 — The Guardian of Your Requirements</p>
            <div class="footer-links">
                <a href="#">About</a>
                <a href="#">Privacy</a>
                <a href="#">Contact</a>
            </div>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
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

        // Header background on scroll
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.background = 'rgba(255, 255, 255, 0.98)';
            } else {
                header.style.background = 'rgba(255, 255, 255, 0.95)';
            }
        });

        // Add hover effects to cards
        document.querySelectorAll('.solution-item, .benefit-item, .problem-item').forEach(item => {
            item.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-5px) scale(1.02)';
            });
            
            item.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });
    </script>
</body>
</html>
