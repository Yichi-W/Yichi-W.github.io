<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Yichi Wang - Personal Homepage</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --text-color: #333;
            --bg-color: #f8f9fa;
            --card-bg: #ffffff;
            --shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--bg-color);
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: var(--card-bg);
            box-shadow: var(--shadow);
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background: rgba(255,255,255,0.95);
            backdrop-filter: blur(10px);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--primary-color);
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--secondary-color);
        }

        /* Hero Section */
        .hero {
            margin-top: 80px;
            padding: 4rem 2rem;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
        }

        .hero-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .profile-img {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            margin-bottom: 2rem;
            border: 5px solid white;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            object-fit: cover;
        }

        /* Section Styles */
        section {
            padding: 4rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            text-align: center;
            color: var(--primary-color);
            position: relative;
            padding-bottom: 1rem;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: var(--secondary-color);
        }

        /* Cards */
        .card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 2rem;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }

        /* Research Projects Grid */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .project-card {
            background: var(--card-bg);
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .project-card:hover {
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .project-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
        }

        .project-content {
            padding: 1.5rem;
        }

        /* Timeline */
        .timeline {
            position: relative;
            padding: 2rem 0;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            top: 0;
            bottom: 0;
            width: 2px;
            background: var(--secondary-color);
        }

        .timeline-item {
            position: relative;
            padding: 1rem 2rem;
            width: 45%;
            margin-bottom: 2rem;
            background: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
        }

        .timeline-item:nth-child(odd) {
            left: 0;
        }

        .timeline-item:nth-child(even) {
            left: 55%;
        }

        .timeline-date {
            font-weight: bold;
            color: var(--secondary-color);
            margin-bottom: 0.5rem;
        }

        /* Skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .skill-category {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
        }

        .skill-list {
            list-style: none;
            margin-top: 1rem;
        }

        .skill-list li {
            padding: 0.5rem 0;
            border-bottom: 1px solid #eee;
        }

        .skill-list li:last-child {
            border-bottom: none;
        }

        /* Publications */
        .publication-item {
            background: var(--card-bg);
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border-radius: 10px;
            box-shadow: var(--shadow);
            border-left: 4px solid var(--secondary-color);
        }

        .publication-title {
            font-weight: bold;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
        }

        .publication-authors {
            font-style: italic;
            color: #666;
            margin-bottom: 0.5rem;
        }

        .publication-venue {
            color: var(--secondary-color);
        }

        /* Awards */
        .awards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .award-item {
            text-align: center;
            padding: 1.5rem;
            background: var(--card-bg);
            border-radius: 10px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .award-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.15);
        }

        .award-icon {
            font-size: 3rem;
            color: var(--accent-color);
            margin-bottom: 1rem;
        }

        /* Contact */
        .contact-info {
            display: flex;
            justify-content: center;
            gap: 3rem;
            flex-wrap: wrap;
            margin-top: 2rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 1rem;
            font-size: 1.1rem;
        }

        .contact-item i {
            color: var(--secondary-color);
            font-size: 1.5rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .timeline::before {
                left: 20px;
            }

            .timeline-item {
                width: calc(100% - 40px);
                left: 40px !important;
            }

            .hero {
                padding: 2rem 1rem;
            }

            section {
                padding: 2rem 1rem;
            }
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

        .fade-in-up {
            animation: fadeInUp 0.6s ease-out;
        }

        /* Smooth scroll */
        html {
            scroll-behavior: smooth;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav id="navbar">
        <div class="nav-container">
            <h2>Yichi Wang</h2>
            <ul class="nav-links">
                <li><a href="#home">首页</a></li>
                <li><a href="#about">关于我</a></li>
                <li><a href="#education">教育背景</a></li>
                <li><a href="#research">研究经历</a></li>
                <li><a href="#publications">发表论文</a></li>
                <li><a href="#projects">项目展示</a></li>
                <li><a href="#awards">荣誉奖项</a></li>
                <li><a href="#skills">技能</a></li>
                <li><a href="#contact">联系方式</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content fade-in-up">
            <img src="profile-photo.jpg" alt="Yichi Wang" class="profile-img">
            <h1>王一驰 | Yichi Wang</h1>
            <p style="font-size: 1.2rem; margin-top: 1rem;">北京工业大学 人工智能专业 大三本科生</p>
            <p style="font-size: 1.1rem; margin-top: 0.5rem;">Beijing University of Technology | Artificial Intelligence</p>
            <div style="margin-top: 2rem;">
                <a href="https://scholar.google.com/citations?user=YOUR_ID" target="_blank" style="color: white; margin: 0 1rem; font-size: 1.5rem;">
                    <i class="fab fa-google"></i>
                </a>
                <a href="https://github.com/YOUR_GITHUB" target="_blank" style="color: white; margin: 0 1rem; font-size: 1.5rem;">
                    <i class="fab fa-github"></i>
                </a>
                <a href="https://space.bilibili.com/688302426" target="_blank" style="color: white; margin: 0 1rem; font-size: 1.5rem;">
                    <i class="fab fa-bilibili"></i>
                </a>
                <a href="mailto:mstaryc02@gmail.com" style="color: white; margin: 0 1rem; font-size: 1.5rem;">
                    <i class="fas fa-envelope"></i>
                </a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about">
        <h2 class="section-title">关于我 | About Me</h2>
        <div class="card">
            <p style="font-size: 1.1rem; line-height: 1.8;">
                您好！我是王一驰，目前就读于<strong>北京工业大学</strong>（211工程、双一流）<strong>人工智能专业</strong>大三。
                我的研究兴趣包括：<strong>多模态大语言模型</strong>、<strong>具身智能</strong>和<strong>AI安全应用</strong>。
            </p>
            <p style="font-size: 1.1rem; line-height: 1.8; margin-top: 1rem;">
                我正在积极寻求<strong>2026年秋季入学的MPhil和PhD机会</strong>。我非常乐意有机会进一步讨论我的背景和研究经历。
                同时，我在<a href="https://space.bilibili.com/688302426" target="_blank" style="color: var(--secondary-color);">B站</a>上逐步发布精选论文的算法推导视频，欢迎访问交流。
            </p>
        </div>
    </section>

    <!-- Education Section -->
    <section id="education">
        <h2 class="section-title">教育背景 | Education</h2>
        <div class="timeline">
            <div class="timeline-item">
                <div class="timeline-date">2021.09 - 2025.06（预计）</div>
                <h3>北京工业大学</h3>
                <p><strong>人工智能专业</strong> 本科</p>
                <p>平均分：87.79/100 | GPA: 3.65/4.0 | 专业排名：前15%</p>
                <p>核心课程：高等数学(99)、深度学习(97)、模拟电子技术(92)、复变函数(92)</p>
            </div>
        </div>
    </section>

    <!-- Research Experience Section -->
    <section id="research">
        <h2 class="section-title">研究经历 | Research Experience</h2>
        
        <div class="card">
            <h3>香港科技大学（广州）- 远程研究实习生</h3>
            <p class="timeline-date">2024.09 - 至今</p>
            <p><strong>导师：</strong>徐仁婧教授 (Prof. Renjing Xu)</p>
            <ul style="margin-top: 1rem; margin-left: 2rem;">
                <li>为5个视觉语言模型和4个扩散模型进行漏洞分析，运行评估管道并整合评估指标</li>
                <li>使用单页Web应用开发Jailbreak-AudioBench演示界面，实现结果可视化</li>
                <li>处理13个受害者模型的实验数据，为跨模态大语言模型对抗迁移研究做出贡献</li>
                <li>使用Logit Lens和数据流分析等策略研究VLA模型与VLM的差异</li>
            </ul>
        </div>

        <div class="card">
            <h3>百度飞桨社区北京工业大学负责人</h3>
            <p class="timeline-date">2023 - 至今</p>
            <ul style="margin-top: 1rem; margin-left: 2rem;">
                <li>领导社区参与并协调开源深度学习项目</li>
                <li>组织研讨会、黑客马拉松和教程课程，推动飞桨框架的采用</li>
            </ul>
        </div>

        <div class="card">
            <h3>X-Humanoid真实世界机器人评估参与者</h3>
            <p class="timeline-date">2025.01 - 至今</p>
            <ul style="margin-top: 1rem; margin-left: 2rem;">
                <li>在多种机器人平台上进行具身智能大模型的真实世界基准评估</li>
                <li>在复杂动态环境中测量关键性能指标（延迟、鲁棒性、适应性）</li>
            </ul>
        </div>

        <div class="card">
            <h3>百度机器人创新部门实习生（计划中）</h3>
            <p class="timeline-date">2025.05 - </p>
            <ul style="margin-top: 1rem; margin-left: 2rem;">
                <li>计划探索边缘设备上具身智能的实时部署策略</li>
                <li>将开发并实施边缘AI机器人应用的综合评估框架</li>
            </ul>
        </div>
    </section>

    <!-- Publications Section -->
    <section id="publications">
        <h2 class="section-title">发表论文 | Publications</h2>
        
        <div class="publication-item">
            <div class="publication-title">
                Exploring Typographic Visual Prompts Injection Threats in Cross-Modality Generation Models
            </div>
            <div class="publication-authors">
                H. Cheng, E. Xiao, <strong>Y. Wang</strong>, K. Xu, M. Sun, J. Gu, R. Xu
            </div>
            <div class="publication-venue">
                IJCAI 2025 Workshop (Best Paper Nomination)
            </div>
        </div>

        <div class="publication-item">
            <div class="publication-title">
                Transfer Attack for Bad and Good: Explain and Boost Adversarial Transferability across Multimodal Large Language Models
            </div>
            <div class="publication-authors">
                H. Cheng, E. Xiao, J. Yang, J. Duan, <strong>Y. Wang</strong>, J. Cao, Q. Zhang, L. Yang, K. Xu, J. Gu, R. Xu
            </div>
            <div class="publication-venue">
                ACM MM 2025 (Submission)
            </div>
        </div>

        <h3 style="margin-top: 2rem; margin-bottom: 1rem;">预印本 | Preprints</h3>
        
        <div class="publication-item">
            <div class="publication-title">
                JailbreakAudioBench: In-Depth Evaluation and Analysis of Jailbreak Threats for Large Audio Language Models
            </div>
            <div class="publication-authors">
                H. Cheng, E. Xiao, J. Shao, <strong>Y. Wang</strong>, L. Yang, C. Shen, P. Torr, J. Gu, R. Xu
            </div>
            <div class="publication-venue">
                Submitted to NeurIPS 2025
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <h2 class="section-title">项目展示 | Research Projects</h2>
        
        <div class="projects-grid">
            <div class="project-card">
                <img src="project1-tvp.jpg" alt="Typographic Visual Prompts" class="project-img">
                <div class="project-content">
                    <h3>印刷视觉提示注入威胁研究</h3>
                    <p>探索跨模态生成模型中的印刷视觉提示注入威胁，评估开源和闭源模型的漏洞</p>
                    <p style="margin-top: 0.5rem; color: var(--secondary-color);">IJCAI 2025 最佳论文提名</p>
                </div>
            </div>

            <div class="project-card">
                <img src="project2-transfer.jpg" alt="Transfer Attack" class="project-img">
                <div class="project-content">
                    <h3>跨模态对抗迁移研究</h3>
                    <p>设计新型迁移攻击框架，系统评估多模态大语言模型间的对抗迁移性</p>
                    <p style="margin-top: 0.5rem; color: var(--secondary-color);">ACM MM 2025 投稿</p>
                </div>
            </div>

            <div class="project-card">
                <img src="project3-audio.jpg" alt="JailbreakAudioBench" class="project-img">
                <div class="project-content">
                    <h3>音频越狱基准测试平台</h3>
                    <p>首个全面的音频越狱基准测试平台，开发交互式Web界面和评估管道</p>
                    <p style="margin-top: 0.5rem; color: var(--secondary-color);">NeurIPS 2025 投稿</p>
                </div>
            </div>

            <div class="project-card">
                <img src="project4-vla.jpg" alt="VLA Interpretability" class="project-img">
                <div class="project-content">
                    <h3>视觉语言动作模型可解释性</h3>
                    <p>研究VLA模型的可解释性，通过Logit Lens等方法分析模型内部机制</p>
                    <p style="margin-top: 0.5rem; color: var(--secondary-color);">进行中</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Awards Section -->
    <section id="awards">
        <h2 class="section-title">荣誉奖项 | Honors & Awards</h2>
        
        <div class="awards-grid">
            <div class="award-item">
                <i class="fas fa-trophy award-icon"></i>
                <h4>IJCAI 2025 Workshop</h4>
                <p>最佳论文提名</p>
            </div>
            
            <div class="award-item">
                <i class="fas fa-medal award-icon"></i>
                <h4>校级优秀奖学金</h4>
                <p>2022年、2024年</p>
            </div>
            
            <div class="award-item">
                <i class="fas fa-star award-icon"></i>
                <h4>优秀学生</h4>
                <p>2022年</p>
            </div>
            
            <div class="award-item">
                <i class="fas fa-award award-icon"></i>
                <h4>Datawhale AI夏令营</h4>
                <p>一等奖（前5%）</p>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills">
        <h2 class="section-title">技能 | Skills</h2>
        
        <div class="skills-grid">
            <div class="skill-category">
                <h3><i class="fas fa-code"></i> 编程语言</h3>
                <ul class="skill-list">
                    <li>Python（熟练）- PyTorch, NumPy, Pandas</li>
                    <li>JavaScript/HTML/CSS - Web开发</li>
                    <li>C/C++ - 算法实现</li>
                    <li>MATLAB - 数据分析</li>
                </ul>
            </div>
            
            <div class="skill-category">
                <h3><i class="fas fa-brain"></i> AI/ML框架</h3>
                <ul class="skill-list">
                    <li>PyTorch - 深度学习模型开发</li>
                    <li>PaddlePaddle - 框架使用与推广</li>
                    <li>Transformers - 大语言模型</li>
                    <li>OpenCV - 计算机视觉</li>
                </ul>
            </div>
            
            <div class="skill-category">
                <h3><i class="fas fa-tools"></i> 工具与技能</h3>
                <ul class="skill-list">
                    <li>Git/GitHub - 版本控制</li>
                    <li>Linux - 系统管理</li>
                    <li>Docker - 容器化部署</li>
                    <li>LaTeX - 学术写作</li>
                </ul>
            </div>
            
            <div class="skill-category">
                <h3><i class="fas fa-language"></i> 语言能力</h3>
                <ul class="skill-list">
                    <li>中文 - 母语</li>
                    <li>英语 - 流利（学术交流）</li>
                    <li>日语 - 初级</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
        <h2 class="section-title">联系方式 | Contact</h2>
        
        <div class="contact-info">
            <div class="contact-item">
                <i class="fas fa-envelope"></i>
                <div>
                    <p>mstaryc02@gmail.com</p>
                    <p>wangyc2002@emails.bjut.edu.cn</p>
                </div>
            </div>
            
            <div class="contact-item">
                <i class="fas fa-map-marker-alt"></i>
                <p>北京市朝阳区 北京工业大学</p>
            </div>
            
            <div class="contact-item">
                <i class="fab fa-bilibili"></i>
                <a href="https://space.bilibili.com/688302426" target="_blank">B站主页</a>
            </div>
        </div>
    </section>

    <script>
        // Navbar scroll effect
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Smooth scroll for navigation links
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

        // Intersection Observer for fade-in animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -100px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe all cards and sections
        document.querySelectorAll('.card, .project-card, .timeline-item, .award-item, .skill-category, .publication-item').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'all 0.6s ease-out';
            observer.observe(el);
        });
    </script>
</body>
</html>
