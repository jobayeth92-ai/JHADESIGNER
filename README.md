<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:b="http://www.google.com/2005/gml/b"
      xmlns:data="http://www.google.com/2005/gml/data"
      xmlns:expr="http://www.google.com/2005/gml/expr"
      b:version="2"
      b:templateVersion="1.0.0"
      b:responsive="true"
      b:layoutsVersion="3"
      lang="en">

<head>
  <b:include data="blog" name="all-head-content"/>
  <title><data:blog.pageTitle/></title>
  <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- Google Fonts: Hind Siliguri -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="crossorigin" />
    <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@300;400;500;600;700&amp;display=swap" rel="stylesheet" />
    
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#3a86ff',
                        secondary: '#8338ec',
                        dark: '#0f172a',
                        darklight: '#1e293b',
                        accent: '#ff007f'
                    },
                    fontFamily: {
                        sans: ['"Hind Siliguri"', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />

    <!-- AOS (Animate On Scroll) Library CSS -->
    <link rel="stylesheet" href="https://unpkg.com/aos@next/dist/aos.css" />

    <style><![CDATA[
        body {
            font-family: 'Hind Siliguri', sans-serif;
            background-color: #0b0f19;
            color: #f1f5f9;
            overflow-x: hidden;
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #0b0f19;
        }
        ::-webkit-scrollbar-thumb {
            background: #3a86ff;
            border-radius: 4px;
        }

        /* Gradient Text Effect */
        .text-gradient {
            background: linear-gradient(135deg, #3a86ff 0%, #8338ec 50%, #ff007f 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        /* Gradient Button Effect */
        .btn-gradient {
            background: linear-gradient(135deg, #3a86ff 0%, #8338ec 100%);
            transition: all 0.4s ease;
            position: relative;
            z-index: 1;
            overflow: hidden;
        }
        .btn-gradient::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: linear-gradient(135deg, #8338ec 0%, #ff007f 100%);
            z-index: -1;
            transition: opacity 0.4s ease;
            opacity: 0;
        }
        .btn-gradient:hover::before {
            opacity: 1;
        }
        .btn-gradient:hover {
            box-shadow: 0 10px 25px -5px rgba(58, 134, 255, 0.5);
            transform: translateY(-2px);
        }

        /* Hero Parallax Glow Background */
        .parallax-bg {
            background: radial-gradient(circle at 50% 30%, rgba(58, 134, 255, 0.15) 0%, rgba(131, 56, 236, 0.05) 50%, transparent 70%);
        }

        /* Glassmorphism Card */
        .glass-card {
            background: rgba(30, 41, 59, 0.6);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 1rem;
        }

        /* Portfolio Image Auto-Scroll on Hover Effect */
        .portfolio-img-container {
            position: relative;
            overflow: hidden;
            height: 380px;
            border-radius: 0.75rem;
        }
        .portfolio-img-container img {
            width: 100%;
            height: auto;
            position: absolute;
            top: 0;
            left: 0;
            transition: transform 4s ease-in-out;
        }
        .portfolio-img-container:hover img {
            transform: translateY(calc(-100% + 380px));
        }

        /* Floating Animation */
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-12px); }
        }
        .animate-float {
            animation: float 4s ease-in-out infinite;
        }
    ]]></style>
</head>

<body class="antialiased">
  <!-- Blogger-required section; the portfolio itself is static HTML below. -->
  <b:section id="blogger-required-section" class="hidden" maxwidgets="1" showaddelement="no"></b:section>

  <!-- Header / Navbar -->
    <header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 backdrop-blur-md bg-opacity-80 bg-[#0b0f19]/80 border-b border-white/10">
        <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
            <a href="#home" class="text-2xl font-bold tracking-wider text-gradient font-sans flex items-center gap-2">
                <i class="fa-solid me-1 fa-palette text-primary"></i> <span id="nav-brand-name">Jobayet Hasan</span>
            </a>
            
            <!-- Desktop Nav -->
            <nav class="hidden md:flex space-x-8 text-slate-300 font-medium text-lg">
                <a href="#home" class="hover:text-primary transition-colors">Home</a>
                <a href="#about" class="hover:text-primary transition-colors">About</a>
                <a href="#services" class="hover:text-primary transition-colors">Services</a>
                <a href="#portfolio" class="hover:text-primary transition-colors">Portfolio</a>
                <a href="#contact" class="hover:text-primary transition-colors">Contact</a>
            </nav>

            <a href="#contact" class="hidden md:inline-flex btn-gradient text-white px-6 py-2.5 rounded-full font-semibold shadow-lg items-center gap-2">
                <span>Hire Me</span> <i class="fa-solid fa-arrow-right"></i>
            </a>

            <!-- Mobile Menu Toggle -->
            <button id="mobile-menu-btn" class="md:hidden text-2xl text-slate-200 focus:outline-none">
                <i class="fa-solid fa-bars"></i>
            </button>
        </div>

        <!-- Mobile Menu Dropdown -->
        <div id="mobile-menu" class="hidden md:hidden bg-darklight/95 border-b border-white/10 px-6 py-4 flex flex-col space-y-4 text-slate-200 font-medium">
            <a href="#home" class="mobile-nav-link hover:text-primary transition-colors">Home</a>
            <a href="#about" class="mobile-nav-link hover:text-primary transition-colors">About</a>
            <a href="#services" class="mobile-nav-link hover:text-primary transition-colors">Services</a>
            <a href="#portfolio" class="mobile-nav-link hover:text-primary transition-colors">Portfolio</a>
            <a href="#contact" class="mobile-nav-link hover:text-primary transition-colors">Contact</a>
        </div>
    </header>

    <!-- Hero Section with Parallax Effect -->
    <section id="home" class="relative min-h-screen flex items-center pt-24 pb-12 parallax-bg overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-12 gap-12 items-center w-full relative z-10">
            
            <!-- Left Text Content -->
            <div class="lg:col-span-7 space-y-6 text-center lg:text-left" data-aos="fade-right" data-aos-duration="1000">
                <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full glass-card border-primary/30 text-primary font-medium text-sm tracking-wide">
                    <span class="w-2.5 h-2.5 rounded-full bg-primary animate-ping"></span>
                    Available For Freelance &amp; Full-time Projects
                </div>
                
                <h1 class="text-4xl sm:text-6xl font-extrabold text-white leading-tight">
                    Hello, I'm <br class="hidden sm:inline" />
                    <span class="text-gradient" id="hero-name">Jobayet Hasan</span>
                </h1>
                
                <p class="text-2xl sm:text-3xl font-semibold text-slate-300">
                    Professional <span id="hero-title" class="text-primary border-b-2 border-primary">Graphic Designer</span>
                </p>

                <p id="hero-bio" class="text-slate-400 text-lg max-w-2xl leading-relaxed mx-auto lg:mx-0">
                    Transforming ideas into visually stunning brand identities. Specializing in Brand Kits, Media Kits, Logos, Social Media Graphics, Flyers, Business Cards, and Corporate Stationery.
                </p>

                <div class="pt-4 flex flex-wrap gap-4 justify-center lg:justify-start">
                    <a href="#contact" class="btn-gradient text-white px-8 py-3.5 rounded-full font-bold text-lg flex items-center gap-3 shadow-xl">
                        <i class="fa-solid fa-paper-plane"></i> Let's Work Together
                    </a>
                    <a href="#portfolio" class="px-8 py-3.5 rounded-full font-bold text-lg text-white glass-card hover:bg-white/10 transition-all flex items-center gap-3 border border-white/20">
                        <i class="fa-solid fa-briefcase text-primary"></i> View My Work
                    </a>
                </div>

                <!-- Stats counter -->
                <div class="grid grid-cols-3 gap-4 pt-8 border-t border-white/10 max-w-lg mx-auto lg:mx-0">
                    <div>
                        <h3 class="text-3xl font-bold text-white">500+</h3>
                        <p class="text-slate-400 text-sm">Projects Completed</p>
                    </div>
                    <div>
                        <h3 class="text-3xl font-bold text-white">100%</h3>
                        <p class="text-slate-400 text-sm">Client Satisfaction</p>
                    </div>
                    <div>
                        <h3 class="text-3xl font-bold text-white">5+</h3>
                        <p class="text-slate-400 text-sm">Years Experience</p>
                    </div>
                </div>
            </div>

            <!-- Right Profile Image Card -->
            <div class="lg:col-span-5 flex justify-center" data-aos="fade-left" data-aos-duration="1000">
                <div class="relative w-72 h-72 sm:w-96 sm:h-96">
                    <!-- Glow effect behind image -->
                    <div class="absolute -inset-4 rounded-full bg-gradient-to-r from-primary to-secondary opacity-40 blur-2xl animate-pulse"></div>
                    
                    <!-- Profile Photo Box -->
                    <div class="relative w-full h-full rounded-3xl overflow-hidden glass-card p-3 border-2 border-primary/40 shadow-2xl">
                        <img id="hero-profile-img" src="" alt="Jobayet Hasan" class="w-full h-full object-cover rounded-2xl shadow-inner hover:scale-105 transition-transform duration-500" />
                    </div>

                    <!-- Floating Badge 1 -->
                    <div class="absolute -bottom-4 -left-4 glass-card p-4 flex items-center gap-3 shadow-2xl animate-float">
                        <div class="w-12 h-12 rounded-xl bg-primary/20 flex items-center justify-center text-primary text-2xl">
                            <i class="fa-solid fa-wand-magic-sparkles"></i>
                        </div>
                        <div>
                            <p class="text-xs text-slate-400 font-medium">Creative Mind</p>
                            <p class="text-sm font-bold text-white">Brand Strategist</p>
                        </div>
                    </div>

                    <!-- Floating Badge 2 -->
                    <div class="absolute -top-4 -right-4 glass-card p-3 px-4 flex items-center gap-2 shadow-2xl animate-float" style="animation-delay: 2s;">
                        <i class="fa-solid fa-star text-yellow-400"></i>
                        <span class="text-xs font-bold text-white">Top Rated Designer</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Services Section -->
    <section id="services" class="py-24 relative bg-darklight/40">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center max-w-3xl mx-auto mb-16" data-aos="fade-up">
                <h2 class="text-sm uppercase font-bold text-primary tracking-widest mb-2">My Expertise</h2>
                <h3 class="text-3xl sm:text-5xl font-extrabold text-white">Specialized Graphic Services</h3>
                <div class="w-20 h-1.5 bg-gradient-to-r from-primary to-secondary mx-auto mt-4 rounded-full"></div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Service 1 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-primary" data-aos="fade-up" data-aos-delay="100">
                    <div class="w-16 h-16 rounded-2xl bg-primary/10 text-primary group-hover:bg-primary group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-vector-square"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">Logo &amp; Brand Identity</h4>
                    <p class="text-slate-400 leading-relaxed">
                        Designing impactful, modern logos and comprehensive brand guidelines that make your business stand out uniquely in the market.
                    </p>
                </div>

                <!-- Service 2 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-secondary" data-aos="fade-up" data-aos-delay="200">
                    <div class="w-16 h-16 rounded-2xl bg-secondary/10 text-secondary group-hover:bg-secondary group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-box-open"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">Media Kit &amp; Brand Kit</h4>
                    <p class="text-slate-400 leading-relaxed">
                        Complete press kits, media kits, media release sheets, and brand collateral tailored for influencers, creators, and businesses.
                    </p>
                </div>

                <!-- Service 3 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-accent" data-aos="fade-up" data-aos-delay="300">
                    <div class="w-16 h-16 rounded-2xl bg-pink-500/10 text-pink-500 group-hover:bg-pink-500 group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-hashtag"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">Social Media Design</h4>
                    <p class="text-slate-400 leading-relaxed">
                        Eye-catching social media posts, banners, covers, stories, and ad graphics designed for Instagram, Facebook, and LinkedIn.
                    </p>
                </div>

                <!-- Service 4 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-primary" data-aos="fade-up" data-aos-delay="400">
                    <div class="w-16 h-16 rounded-2xl bg-primary/10 text-primary group-hover:bg-primary group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-id-card"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">Business Card &amp; Letterhead</h4>
                    <p class="text-slate-400 leading-relaxed">
                        Professional, print-ready corporate identity assets including executive business cards, official letterheads, and envelopes.
                    </p>
                </div>

                <!-- Service 5 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-secondary" data-aos="fade-up" data-aos-delay="500">
                    <div class="w-16 h-16 rounded-2xl bg-secondary/10 text-secondary group-hover:bg-secondary group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-scroll"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">Flyer &amp; Brochure Design</h4>
                    <p class="text-slate-400 leading-relaxed">
                        High-conversion promotional flyers, posters, bi-fold, and tri-fold brochures for events, product launches, and corporate promotion.
                    </p>
                </div>

                <!-- Service 6 -->
                <div class="glass-card p-8 hover:-translate-y-2 transition-all duration-300 group border-t-2 border-t-transparent hover:border-t-accent" data-aos="fade-up" data-aos-delay="600">
                    <div class="w-16 h-16 rounded-2xl bg-pink-500/10 text-pink-500 group-hover:bg-pink-500 group-hover:text-white flex items-center justify-center text-3xl mb-6 transition-all duration-300">
                        <i class="fa-solid fa-layer-group"></i>
                    </div>
                    <h4 class="text-2xl font-bold text-white mb-3">All Media Kits &amp; Print</h4>
                    <p class="text-slate-400 leading-relaxed">
                        End-to-end design solutions covering all printable and digital marketing materials crafted with precision and creativity.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <!-- Portfolio Section with Image Hover Scroll Effect -->
    <section id="portfolio" class="py-24 relative">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center max-w-3xl mx-auto mb-16" data-aos="fade-up">
                <h2 class="text-sm uppercase font-bold text-primary tracking-widest mb-2">My Creative Works</h2>
                <h3 class="text-3xl sm:text-5xl font-extrabold text-white">Featured Portfolio Showcase</h3>
                <p class="text-slate-400 mt-4 text-base">Hover over the project cards below to automatically scroll through full designs!</p>
                <div class="w-20 h-1.5 bg-gradient-to-r from-primary to-secondary mx-auto mt-4 rounded-full"></div>
            </div>

            <div id="portfolio-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <!-- Portfolio items dynamically rendered via JS -->
            </div>
        </div>
    </section>

    <!-- Contact &amp; Form Section -->
    <section id="contact" class="py-24 relative bg-darklight/40">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center max-w-3xl mx-auto mb-16" data-aos="fade-up">
                <h2 class="text-sm uppercase font-bold text-primary tracking-widest mb-2">Get In Touch</h2>
                <h3 class="text-3xl sm:text-5xl font-extrabold text-white">Let's Discuss Your Project</h3>
                <div class="w-20 h-1.5 bg-gradient-to-r from-primary to-secondary mx-auto mt-4 rounded-full"></div>
            </div>

            <div class="grid grid-cols-1 lg:grid-cols-12 gap-12">
                <!-- Contact Info Cards -->
                <div class="lg:col-span-5 space-y-6" data-aos="fade-right">
                    <div class="glass-card p-6 flex items-center gap-5 hover:border-primary/50 transition-colors">
                        <div class="w-14 h-14 rounded-2xl bg-primary/20 text-primary flex items-center justify-center text-2xl shrink-0">
                            <i class="fa-solid fa-phone"></i>
                        </div>
                        <div>
                            <p class="text-xs uppercase font-semibold text-slate-400">Phone</p>
                            <a id="contact-phone-link" href="#" class="text-lg font-bold text-white hover:text-primary transition-colors">
                                <span id="contact-phone"></span>
                            </a>
                        </div>
                    </div>

                    <div class="glass-card p-6 flex items-center gap-5 hover:border-primary/50 transition-colors">
                        <div class="w-14 h-14 rounded-2xl bg-secondary/20 text-secondary flex items-center justify-center text-2xl shrink-0">
                            <i class="fa-solid fa-envelope"></i>
                        </div>
                        <div>
                            <p class="text-xs uppercase font-semibold text-slate-400">Email Address</p>
                            <a id="contact-email-link" href="#" class="text-lg font-bold text-white hover:text-primary transition-colors">
                                <span id="contact-email"></span>
                            </a>
                        </div>
                    </div>

                    <div class="glass-card p-6 flex items-center gap-5 hover:border-primary/50 transition-colors">
                        <div class="w-14 h-14 rounded-2xl bg-pink-500/20 text-pink-500 flex items-center justify-center text-2xl shrink-0">
                            <i class="fa-solid fa-location-dot"></i>
                        </div>
                        <div>
                            <p class="text-xs uppercase font-semibold text-slate-400">Location</p>
                            <p id="contact-location" class="text-lg font-bold text-white"></p>
                        </div>
                    </div>

                    <div class="glass-card p-6 flex items-center gap-5 hover:border-emerald-500/50 transition-colors">
                        <div class="w-14 h-14 rounded-2xl bg-emerald-500/20 text-emerald-400 flex items-center justify-center text-2xl shrink-0">
                            <i class="fa-brands fa-whatsapp"></i>
                        </div>
                        <div>
                            <p class="text-xs uppercase font-semibold text-slate-400">Direct WhatsApp</p>
                            <a id="whatsapp-direct-btn" href="#" target="_blank" class="text-lg font-bold text-emerald-400 hover:underline">
                                Chat on WhatsApp
                            </a>
                        </div>
                    </div>
                </div>

                <!-- Contact Form -->
                <div class="lg:col-span-7" data-aos="fade-left">
                    <form id="portfolio-contact-form" class="glass-card p-8 sm:p-10 space-y-6 border border-white/10 shadow-2xl">
                        <h4 class="text-2xl font-bold text-white mb-2">Send Me A Message</h4>
                        <p class="text-slate-400 text-sm mb-6">Submitting will automatically log your request to our Google System and open WhatsApp with your message instantly!</p>

                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium text-slate-300 mb-2">Your Name</label>
                                <div class="relative">
                                    <span class="absolute left-4 top-3.5 text-slate-500"><i class="fa-solid fa-user"></i></span>
                                    <input type="text" id="form-name" required="required" placeholder="John Doe" class="w-full pl-11 pr-4 py-3 bg-dark/70 border border-white/10 rounded-xl text-white placeholder-slate-500 focus:outline-none focus:border-primary transition-colors" />
                                </div>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-slate-300 mb-2">Phone Number</label>
                                <div class="relative">
                                    <span class="absolute left-4 top-3.5 text-slate-500"><i class="fa-solid fa-phone"></i></span>
                                    <input type="tel" id="form-phone" required="required" placeholder="01700000000" class="w-full pl-11 pr-4 py-3 bg-dark/70 border border-white/10 rounded-xl text-white placeholder-slate-500 focus:outline-none focus:border-primary transition-colors" />
                                </div>
                            </div>
                        </div>

                        <div>
                            <label class="block text-sm font-medium text-slate-300 mb-2">Email Address</label>
                            <div class="relative">
                                <span class="absolute left-4 top-3.5 text-slate-500"><i class="fa-solid fa-envelope"></i></span>
                                <input type="email" id="form-email" required="required" placeholder="john@example.com" class="w-full pl-11 pr-4 py-3 bg-dark/70 border border-white/10 rounded-xl text-white placeholder-slate-500 focus:outline-none focus:border-primary transition-colors" />
                            </div>
                        </div>

                        <div>
                            <label class="block text-sm font-medium text-slate-300 mb-2">Your Message</label>
                            <div class="relative">
                                <span class="absolute left-4 top-3.5 text-slate-500"><i class="fa-solid fa-comment"></i></span>
                                <textarea id="form-message" rows="4" required="required" placeholder="Write your project details here..." class="w-full pl-11 pr-4 py-3 bg-dark/70 border border-white/10 rounded-xl text-white placeholder-slate-500 focus:outline-none focus:border-primary transition-colors"></textarea>
                            </div>
                        </div>

                        <button type="submit" class="w-full btn-gradient text-white py-4 rounded-xl font-bold text-lg shadow-xl flex items-center justify-center gap-3">
                            <i class="fa-solid fa-paper-plane"></i> Submit &amp; Chat on WhatsApp
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Google Map Section -->
    <section class="py-12 bg-dark relative">
        <div class="max-w-7xl mx-auto px-6" data-aos="fade-up">
            <div class="glass-card overflow-hidden p-3 border border-white/10 shadow-2xl">
                <h4 class="text-xl font-bold text-white mb-4 px-3 flex items-center gap-2">
                    <i class="fa-solid fa-map-location-dot text-primary"></i> My Location Map
                </h4>
                <div class="w-full h-80 rounded-xl overflow-hidden">
                    <iframe id="google-map-iframe" src="" class="w-full h-full border-0" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="py-8 bg-[#070a11] border-t border-white/10 text-center text-slate-400">
        <div class="max-w-7xl mx-auto px-6 flex flex-col sm:flex-row justify-between items-center gap-4">
            <p>&#169; 2026 <span id="footer-name" class="text-white font-semibold">Jobayet Hasan</span>. All Rights Reserved.</p>
            <div class="flex space-x-6 text-xl">
                <a href="#" class="hover:text-primary transition-colors"><i class="fa-brands fa-facebook"></i></a>
                <a href="#" class="hover:text-primary transition-colors"><i class="fa-brands fa-behance"></i></a>
                <a href="#" class="hover:text-primary transition-colors"><i class="fa-brands fa-linkedin"></i></a>
                <a href="#" class="hover:text-primary transition-colors"><i class="fa-brands fa-dribbble"></i></a>
            </div>
        </div>
    </footer>


    <!-- AOS Animation Library JS -->
    <script src="https://unpkg.com/aos@next/dist/aos.js"><![CDATA[]]></script>
    
    <!-- Centralized JS Variables &amp; Application Scripts -->
    <script><![CDATA[
        // =========================================================================
        // EDITABLE PERSONAL INFORMATION & API CONFIGURATION VARIABLES
        // Easily update all details from this single JS configuration block!
        // =========================================================================
        const PORTFOLIO_CONFIG = {
            name: "Jobayet Hasan",
            title: "Graphic Designer",
            phone: "01734306345",
            email: "jobayeth92@gmail.com",
            location: "Dhaka, Demo Location",
            whatsappNumber: "8801734306345", // Country code included (880...)
            
            // Profile & Hero Image
            profileImage: "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjo-EzNwTyPtVLDlPeYEpoSJjt7GqYYvqEOk9-D42y-Tp4e6zII0OZj5YfprbkFQSbw9yfFmB6sH8HImN_EJeBm2UPoe4tPzBCicqUPQOopl2NurKHXFoUwMia7Etw-kVtY0E-vnebgUOZ53ja_Q4ANOs_QtUlq1_d4JHzgpJXlFXR5cL8dBoNdtCOpcn8/s1600/ChatGPT%20Image%20Jun%2018,%202026,%2009_12_50%20PM.png",
            
            // Project Portfolio Images
            projects: [
                {
                    title: "Brand Kit & Visual Identity Design",
                    category: "Brand Kit / Logo",
                    image: "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEioiVFdgjzkMLm2eHAtBQOcE71XBzJZ6pIXe80-YDjc130rbAvqIHrn1oEy5e9_WhzCWkX45kPsrRV4wroOYRnsvpVGo1JrNdflkBOxqIWlprw-stLA65fomZ0bRfXoYwE1fId6w2tBCnXJ3RLIuYPNg2fvwn2WvLVLNvjw_IYdiWj0zEsN0Qxr_2cld7c/s1600/portfolio%201%20(1).png"
                },
                {
                    title: "Media Kit & Corporate Stationery",
                    category: "Media Kit / Letterhead",
                    image: "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhJfMiuD6hTilmzrTSMuRfYCgPISiGCun1GxLxZsnTfNsXCNGjhN0zwWU0voIVoslJQvQM_c7jt1LM3I9wDH45pv70SGhQSVIE9D9a-SGGy9t1D1VqvOSENjUHmwq5JHaQg88CDisRJuSEQ8xSC7FQJNthPLwZ-eg_gZS3dhS-3LopIpMx3YJfhOhgmAM/s1600/portfolio%201%20(2).jpg"
                },
                {
                    title: "Flyer & Social Media Banner",
                    category: "Flyer / Social Media",
                    image: "https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg1LOVOZDMQlZ1D5f77qDonLGy1Mm0bcoLiFO0o2-zUl2zYwZYmKdKS_Ycw-zAe9Jd-LTJ4SNrf7GG0J-7iZO6mOrmWtUnvHhGlNUYr2jP0rGAm4qVltB6hhxl82SghE3EBBvXdwAjCKll-s628_cltUSHeyQSUuNLZ1fnfFNdfQYN7mWdDpxCAcyE9fHs/s1600/portfolio%201%20(1).jpg"
                }
            ],

            // Google Map Embed URL
            mapEmbedUrl: "https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d233667.8223908687!2d90.2548722744383!3d23.780887456203027!2m3!1f0!1f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3755b8b087026b81%3A0x8fa563bbdd5904c2!3sDhaka!5e0!3m2!1sen!2sbd!4v1710000000000",

            // Google Script API Endpoint (For saving form data into Google Sheet / Google Forms)
            googleScriptApiUrl: "https://script.google.com/macros/s/AKfycbxYOUR_SCRIPT_ID_HERE/exec",
            
            // Telegram Bot API (Optional integration)
            telegramApiToken: "",
            telegramChatId: ""
        };

        // =========================================================================
        // DOM INITIALIZATION & DYNAMIC BINDING
        // =========================================================================
        document.addEventListener("DOMContentLoaded", function () {
            // Initialize AOS Animation
            AOS.init({
                duration: 800,
                once: true,
            });

            // Populate Info from JS Variables
            document.getElementById("nav-brand-name").innerText = PORTFOLIO_CONFIG.name;
            document.getElementById("hero-name").innerText = PORTFOLIO_CONFIG.name;
            document.getElementById("hero-title").innerText = PORTFOLIO_CONFIG.title;
            document.getElementById("hero-profile-img").src = PORTFOLIO_CONFIG.profileImage;
            document.getElementById("contact-phone").innerText = PORTFOLIO_CONFIG.phone;
            document.getElementById("contact-phone-link").href = "tel:" + PORTFOLIO_CONFIG.phone;
            document.getElementById("contact-email").innerText = PORTFOLIO_CONFIG.email;
            document.getElementById("contact-email-link").href = "mailto:" + PORTFOLIO_CONFIG.email;
            document.getElementById("contact-location").innerText = PORTFOLIO_CONFIG.location;
            document.getElementById("footer-name").innerText = PORTFOLIO_CONFIG.name;
            document.getElementById("whatsapp-direct-btn").href = "https://wa.me/" + PORTFOLIO_CONFIG.whatsappNumber;
            document.getElementById("google-map-iframe").src = PORTFOLIO_CONFIG.mapEmbedUrl;

            // Render Portfolio Grid
            const portfolioGrid = document.getElementById("portfolio-grid");
            PORTFOLIO_CONFIG.projects.forEach((proj, idx) => {
                const cardHtml = `
                    <div class="glass-card overflow-hidden group border border-white/10 hover:border-primary/50 transition-all duration-300" data-aos="fade-up" data-aos-delay="${(idx + 1) * 150}">
                        <div class="portfolio-img-container">
                            <img src="${proj.image}" alt="${proj.title}" loading="lazy" />
                        </div>
                        <div class="p-6">
                            <span class="text-xs font-semibold uppercase text-primary tracking-wider">${proj.category}</span>
                            <h4 class="text-xl font-bold text-white mt-1 group-hover:text-primary transition-colors">${proj.title}</h4>
                            <div class="mt-4 flex justify-between items-center">
                                <span class="text-xs text-slate-400"><i class="fa-solid fa-arrows-up-down me-1"></i> Hover image to scroll</span>
                                <a href="${proj.image}" target="_blank" class="w-10 h-10 rounded-full bg-white/10 flex items-center justify-center text-white hover:bg-primary transition-colors">
                                    <i class="fa-solid fa-expand"></i>
                                </a>
                            </div>
                        </div>
                    </div>
                `;
                portfolioGrid.innerHTML += cardHtml;
            });

            // Mobile Navigation Toggle
            const mobileBtn = document.getElementById("mobile-menu-btn");
            const mobileMenu = document.getElementById("mobile-menu");
            mobileBtn.addEventListener("click", () => {
                mobileMenu.classList.toggle("hidden");
            });

            document.querySelectorAll(".mobile-nav-link").forEach(link => {
                link.addEventListener("click", () => {
                    mobileMenu.classList.add("hidden");
                });
            });

            // Contact Form Handling (Submit to Google Script + WhatsApp redirect)
            const contactForm = document.getElementById("portfolio-contact-form");
            contactForm.addEventListener("submit", function (e) {
                e.preventDefault();

                const name = document.getElementById("form-name").value.trim();
                const phone = document.getElementById("form-phone").value.trim();
                const email = document.getElementById("form-email").value.trim();
                const message = document.getElementById("form-message").value.trim();

                // 1. Send data to Google Script API (Google Sheet / Form backend) if URL is configured
                if (PORTFOLIO_CONFIG.googleScriptApiUrl && !PORTFOLIO_CONFIG.googleScriptApiUrl.includes("YOUR_SCRIPT_ID_HERE")) {
                    fetch(PORTFOLIO_CONFIG.googleScriptApiUrl, {
                        method: "POST",
                        mode: "no-cors",
                        headers: { "Content-Type": "application/json" },
                        body: JSON.stringify({ name, phone, email, message, timestamp: new Date() })
                    }).catch(err => console.log("Google Script submit error: ", err));
                }

                // 2. Format & Redirect to WhatsApp
                const whatsappMsg = `Hello ${PORTFOLIO_CONFIG.name},\n\nI visited your Portfolio Website and would like to connect with you.\n\n👤 *Name:* ${name}\n📞 *Phone:* ${phone}\n✉️ *Email:* ${email}\n💬 *Message:* ${message}`;
                const whatsappUrl = `https://wa.me/${PORTFOLIO_CONFIG.whatsappNumber}?text=${encodeURIComponent(whatsappMsg)}`;

                // Redirect to WhatsApp
                window.open(whatsappUrl, "_blank");

                alert("Thank you! Your message has been prepared. Redirecting to WhatsApp...");
                contactForm.reset();
            });
        });
    ]]></script>
</body>
</html>
