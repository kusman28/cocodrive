<template>
  <div class="app">

    <!-- NAVBAR -->
    <header class="navbar" :class="{ 'is-scrolled': isScrolled }">
      <div class="container nav-inner">
        <a href="#home" class="brand">
          <img src="/cocodrive-logo.png" alt="CocoDrive" class="brand-icon" />
          <span class="brand-coco">CocoDrive</span>
          <!-- <span class="brand-coco">Coco</span><span class="brand-drive">Drive</span> -->
        </a>
        <nav class="nav-links" :class="{ 'is-open': menuOpen }">
          <a href="#services" @click="menuOpen = false">Services</a>
          <a href="#story" @click="menuOpen = false">Our Story</a>
          <a href="#coverage" @click="menuOpen = false">Coverage</a>
          <a href="#notify" class="nav-btn" @click="menuOpen = false">Get Notified</a>
        </nav>
        <button class="menu-toggle" :class="{ 'is-open': menuOpen }" @click="menuOpen = !menuOpen" aria-label="Toggle menu">
          <span /><span /><span />
        </button>
      </div>
    </header>

    <!-- HERO -->
    <section id="home" class="hero">
      <div class="hero-shapes" aria-hidden="true">
        <span class="hs hs-1" /><span class="hs hs-2" /><span class="hs hs-3" />
      </div>
      <div class="container hero-inner">
        <div class="hero-text">
          <div class="launch-pill">
            <span class="live-dot" />
            Launching Soon &mdash; Zamboanga City
          </div>
          <h1>More Than<br><em>Just Delivery.</em></h1>
          <p>Food, groceries, medicine, documents &mdash; CocoDrive gets it there fast. Born in Curuan, made for every Zamboangue&ntilde;o.</p>
          <div class="hero-chips">
            <span><Utensils :size="15" /> Food Delivery</span>
            <span><Bike :size="15" /> Passenger</span>
            <span><Package :size="15" /> Parcel Delivery</span>
          </div>
          <div class="hero-btns">
            <a href="#notify" class="btn btn-white">Get Early Access →</a>
            <a href="#services" class="btn btn-ghost">Our Services</a>
          </div>
        </div>
        <div class="hero-img">
          <img src="/cocodrive-logo-banner.jpg" alt="CocoDrive – More Than Just Delivery" />
        </div>
      </div>
      <div class="wave-wrap" aria-hidden="true">
        <svg viewBox="0 0 1440 80" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="none">
          <path d="M0,40 C360,80 1080,0 1440,40 L1440,80 L0,80Z" fill="#fff" />
        </svg>
      </div>
    </section>

    <!-- SERVICES -->
    <section id="services" class="section-services">
      <div class="container">
        <div class="sec-head">
          <span class="sec-label">What We Offer</span>
          <h2>Your Ride, Your Food,<br><span>Your Delivery.</span></h2>
          <p>Everything you need, delivered fast across Zamboanga City</p>
        </div>
        <div class="cards">
          <div v-for="s in services" :key="s.name" class="card">
            <div class="card-ico"><component :is="s.icon" :size="30" /></div>
            <h3>{{ s.name }}</h3>
            <p>{{ s.desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- BRAND SHOWCASE -->
    <section class="section-showcase">
      <div class="container">
        <img src="/cocodrive-brand-overview.jpg" alt="CocoDrive – Food, Passenger and Parcel Delivery in Zamboanga City" />
      </div>
    </section>

    <!-- STORY -->
    <section id="story" class="section-story">
      <div class="container story-wrap">
        <div class="story-text">
          <span class="sec-label">Our Story</span>
          <h2>Why <span>Coco</span>Drive?</h2>
          <div v-for="pt in storyPoints" :key="pt.title" class="story-pt">
            <span class="pt-ico"><component :is="pt.icon" :size="24" /></span>
            <div>
              <h4>{{ pt.title }}</h4>
              <p>{{ pt.text }}</p>
            </div>
          </div>
          <blockquote>
            "A coconut tree that quenches your heart with its drink and protects you in its shade from the sun 🌴"
          </blockquote>
        </div>
        <div class="story-img">
          <img src="/cocodrive-logo-meaning.jpg" alt="CocoDrive Logo Meaning – Speed, Coconut Heritage, Happy Customer" />
        </div>
      </div>
    </section>

    <!-- COVERAGE -->
    <section id="coverage" class="section-coverage">
      <div class="container cov-inner">
        <span class="sec-label light">Serving</span>
        <h2>From Curuan to All of <span>Zamboanga City</span></h2>
        <p>Starting from our home in Curuan and growing to cover every corner of Zamboanga City. Food, groceries, medicine, documents &mdash; we bring Zamboanga to your door.</p>
        <div class="stats">
          <div class="stat">
            <b>3+</b>
            <span>Services</span>
          </div>
          <div class="stat-line" />
          <div class="stat">
            <b>1</b>
            <span>City</span>
          </div>
          <div class="stat-line" />
          <div class="stat">
            <b>&#x221E;</b>
            <span>Smiles</span>
          </div>
        </div>
        <div class="cov-tags">
          <span v-for="t in tags" :key="t">{{ t }}</span>
        </div>
      </div>
    </section>

    <!-- NOTIFY CTA -->
    <section id="notify" class="section-notify">
      <div class="container">
        <div class="notify-box">
          <div class="notify-rocket"><Rocket :size="52" /></div>
          <h2>Be the First to Know!</h2>
          <p>CocoDrive is launching very soon in Zamboanga City. Leave your email and we&rsquo;ll notify you the moment we go live!</p>
          <form class="notify-form" @submit.prevent="handleNotify">
            <div class="form-row">
              <input
                v-model="email"
                type="email"
                placeholder="Your email address"
                required
                :disabled="notified"
              />
              <button type="submit" class="btn btn-orange" :disabled="notified">
                {{ notified ? "You're on the list!" : 'Notify Me' }}
              </button>
            </div>
          </form>
          <p v-if="notified" class="success-msg">Thank you! We&rsquo;ll be in touch when CocoDrive launches. 🎉</p>
          <p class="fine-print">No spam &mdash; just your CocoDrive launch notification.</p>
        </div>
      </div>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
      <div class="container">
        <div class="foot-row">
          <div class="foot-brand">
            <img src="/cocodrive-logo.png" alt="CocoDrive" class="foot-logo-img" />
          <span class="foot-logo">Coco<strong>Drive</strong></span>
            <p>More Than Just Delivery</p>
            <p class="foot-loc">Curuan, Zamboanga City, Philippines 🌴</p>
          </div>
          <div class="foot-col">
            <h5>Quick Links</h5>
            <a href="#services">Services</a>
            <a href="#story">Our Story</a>
            <a href="#coverage">Coverage</a>
            <a href="#notify">Get Notified</a>
          </div>
          <div class="foot-col">
            <h5>Follow Us</h5>
            <span v-for="t in tags" :key="t" class="foot-tag">{{ t }}</span>
          </div>
        </div>
        <div class="foot-bottom">
          <p>© 2026 CocoDrive &middot; Made for Zamboangueños &middot; We are from you, for you.</p>
        </div>
      </div>
    </footer>

  </div>
</template>

<script setup>
import { Utensils, Bike, Package, TreePalm, Zap, Smile, Rocket } from '@lucide/vue'

useHead({
  title: 'CocoDrive – More Than Just Delivery | Zamboanga City',
  meta: [
    { name: 'description', content: "CocoDrive is Zamboanga City's delivery super app — food, passenger rides, and parcel delivery from Curuan to all of Zamboanga City." },
    { property: 'og:title', content: 'CocoDrive – More Than Just Delivery' },
    { property: 'og:description', content: 'Food, groceries, medicine, documents — CocoDrive gets it there fast. Born in Curuan, made for every Zamboangueño.' },
    { property: 'og:image', content: '/cocodrive-logo-banner.jpg' },
  ],
  link: [
    { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
    { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
    { rel: 'stylesheet', href: 'https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,500;0,600;0,700;0,800;0,900;1,700;1,900&display=swap' },
  ],
})

const isScrolled = ref(false)
const menuOpen = ref(false)
const email = ref('')
const notified = ref(false)

const services = [
  {
    icon: Utensils,
    name: 'Food Delivery',
    desc: 'Order from your favorite local restaurants and get it delivered hot, fresh, and right to your door.',
  },
  {
    icon: Bike,
    name: 'Passenger',
    desc: 'Book a ride anytime, anywhere in Zamboanga City. Fast, safe, and always affordable.',
  },
  {
    icon: Package,
    name: 'Parcel Delivery',
    desc: 'Send documents, groceries, medicine, and anything else — delivered reliably across the city.',
  },
]

const storyPoints = [
  {
    icon: TreePalm,
    title: 'COCO — Our Roots',
    text: 'COCO stands for Coconut. Zamboanga is the heart of coconuts. We are 100% local — born in Curuan, made for Zamboangueños. The palm leaves on our logo are our pride and tropical heritage.',
  },
  {
    icon: Zap,
    title: 'DRIVE — Fast & Moving',
    text: "The three speed lines mean one thing: SPEED. We don't just deliver — we DRIVE fast to bring your food hot, your groceries fresh, and your essentials on time.",
  },
  {
    icon: Smile,
    title: 'THE SMILE — You',
    text: "Look closely inside the C — you'll see a smile. That smile is you. Our goal is not just to deliver a package, but to deliver happiness.",
  },
]

const tags = ['#CocoDrive', '#ZamboangaCity', '#Curuan', '#SupportLocal', '#MoreThanJustDelivery']

const handleScroll = () => {
  isScrolled.value = window.scrollY > 60
}

const handleNotify = () => {
  if (email.value) {
    notified.value = true
    email.value = ''
  }
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<style>
/* ===== RESET & BASE ===== */
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }
body { font-family: 'Poppins', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; color: #444; line-height: 1.6; }
img { max-width: 100%; display: block; }
a { text-decoration: none; }
button { font-family: inherit; }

/* ===== DESIGN TOKENS ===== */
:root {
  --o:        #F05A28;
  --o-dark:   #C94518;
  --o-light:  #FF7A3D;
  --o-bg:     #FFF3EE;
  --o-border: #FFE0D0;
  --black:    #111;
  --text:     #444;
  --muted:    #888;
  --white:    #fff;
  --rad:      16px;
  --shadow:   0 4px 24px rgba(240,90,40,.12);
  --shadow-lg:0 12px 48px rgba(240,90,40,.18);
}

/* ===== LAYOUT ===== */
.container { max-width: 1160px; margin: 0 auto; padding: 0 24px; }

/* ===== BUTTONS ===== */
.btn {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 13px 28px; border-radius: 50px;
  font-weight: 600; font-size: .95rem; cursor: pointer;
  border: 2px solid transparent; transition: all .25s ease;
  font-family: inherit; line-height: 1;
}
.btn-white  { background: #fff; color: var(--o); border-color: #fff; }
.btn-white:hover  { transform: translateY(-2px); box-shadow: 0 8px 24px rgba(0,0,0,.12); }
.btn-ghost  { background: transparent; color: #fff; border-color: rgba(255,255,255,.5); }
.btn-ghost:hover  { background: rgba(255,255,255,.12); border-color: #fff; transform: translateY(-2px); }
.btn-orange { background: var(--o); color: #fff; border-color: var(--o); }
.btn-orange:hover:not(:disabled) { background: var(--o-dark); border-color: var(--o-dark); transform: translateY(-2px); box-shadow: 0 8px 24px rgba(240,90,40,.35); }
.btn:disabled { opacity: .65; cursor: default; transform: none !important; }

/* ===== SECTION HELPERS ===== */
.sec-label {
  display: inline-block; font-size: .78rem; font-weight: 600;
  letter-spacing: .14em; text-transform: uppercase; color: var(--o); margin-bottom: 10px;
}
.sec-label.light { color: rgba(255,255,255,.75); }
.sec-head { text-align: center; margin-bottom: 56px; }
.sec-head h2 { font-size: clamp(1.9rem, 4vw, 2.8rem); font-weight: 800; color: var(--black); line-height: 1.2; margin-bottom: 14px; }
.sec-head h2 span { color: var(--o); }
.sec-head p { color: var(--muted); font-size: 1.05rem; }

/* ===== NAVBAR ===== */
.navbar {
  position: fixed; inset: 0 0 auto 0; z-index: 200;
  padding: 22px 0; transition: all .3s ease;
}
.navbar.is-scrolled {
  background: rgba(255,255,255,.97); backdrop-filter: blur(16px);
  padding: 14px 0; box-shadow: 0 2px 20px rgba(0,0,0,.08);
}
.nav-inner { display: flex; align-items: center; justify-content: space-between; }

.brand { font-size: 1.5rem; font-weight: 600; letter-spacing: -.01em; display: flex; align-items: center; gap: 10px; font-style: italic;}
.brand-icon { width: 38px; height: 38px; border-radius: 10px; box-shadow: 0 0 0 2px rgba(255,255,255,.25); flex-shrink: 0; }
.brand-coco  { color: #fff; transition: color .3s; }
.brand-drive { color: rgba(255,255,255,.8); transition: color .3s; }
.navbar.is-scrolled .brand-coco  { color: var(--black); }
.navbar.is-scrolled .brand-drive { color: var(--o); }

.nav-links { display: flex; align-items: center; gap: 36px; }
.nav-links a { font-size: .92rem; font-weight: 500; color: rgba(255,255,255,.88); transition: color .25s; }
.nav-links a:hover { color: #fff; }
.navbar.is-scrolled .nav-links a { color: var(--text); }
.navbar.is-scrolled .nav-links a:hover { color: var(--o); }

.nav-btn {
  background: rgba(255,255,255,.18) !important;
  border: 1px solid rgba(255,255,255,.4) !important;
  padding: 9px 22px; border-radius: 50px;
  color: #fff !important;
}
.nav-btn:hover { background: rgba(255,255,255,.28) !important; transform: translateY(-1px); }
.navbar.is-scrolled .nav-btn { background: var(--o) !important; border-color: var(--o) !important; color: #fff !important; }
.navbar.is-scrolled .nav-btn:hover { background: var(--o-dark) !important; }

.menu-toggle {
  display: none; flex-direction: column; gap: 5px;
  background: none; border: none; cursor: pointer; z-index: 201; padding: 4px;
}
.menu-toggle span { display: block; width: 24px; height: 2px; background: #fff; border-radius: 2px; transition: all .3s; }
.navbar.is-scrolled .menu-toggle span { background: var(--black); }
.menu-toggle.is-open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
.menu-toggle.is-open span:nth-child(2) { opacity: 0; }
.menu-toggle.is-open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }

/* ===== HERO ===== */
.hero {
  position: relative;
  background: linear-gradient(135deg, #E04A18 0%, var(--o) 50%, var(--o-light) 100%);
  min-height: 100vh; display: flex; flex-direction: column; overflow: hidden;
}
.hero-shapes { position: absolute; inset: 0; pointer-events: none; overflow: hidden; }
.hs { position: absolute; border-radius: 50%; background: rgba(255,255,255,.07); }
.hs-1 { width: 520px; height: 520px; top: -160px; right: -100px; }
.hs-2 { width: 260px; height: 260px; bottom: 80px; left: -60px; }
.hs-3 { width: 180px; height: 180px; top: 46%; left: 24%; }

.hero-inner {
  flex: 1; display: flex; align-items: center; gap: 64px;
  padding-top: 110px; padding-bottom: 100px;
}
.hero-text { flex: 1; color: #fff; }
.launch-pill {
  display: inline-flex; align-items: center; gap: 10px;
  background: rgba(255,255,255,.15); border: 1px solid rgba(255,255,255,.3);
  padding: 7px 18px; border-radius: 50px;
  font-size: .84rem; font-weight: 500; margin-bottom: 24px;
}
.live-dot {
  width: 8px; height: 8px; border-radius: 50%; background: #7fff00; flex-shrink: 0;
  animation: blink 1.8s ease-in-out infinite;
}
@keyframes blink {
  0%,100% { opacity: 1; transform: scale(1); }
  50%      { opacity: .4; transform: scale(1.4); }
}
.hero-text h1 {
  font-size: clamp(2.8rem, 6vw, 4.8rem); font-weight: 900; line-height: 1.08; margin-bottom: 20px;
}
.hero-text h1 em { font-style: italic; display: block; }
.hero-text > p {
  font-size: clamp(.96rem, 1.8vw, 1.14rem); opacity: .9;
  margin-bottom: 32px; line-height: 1.75; max-width: 460px;
}
.hero-chips { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 36px; }
.hero-chips span {
  display: inline-flex; align-items: center; gap: 7px;
  background: rgba(255,255,255,.15); border: 1px solid rgba(255,255,255,.3);
  padding: 7px 16px; border-radius: 50px; font-size: .88rem; font-weight: 500;
}
.hero-btns { display: flex; flex-wrap: wrap; gap: 14px; }
.hero-img { flex: 0 0 420px; }
.hero-img img { width: 100%; border-radius: 20px; box-shadow: 0 20px 60px rgba(0,0,0,.26); }

.wave-wrap { position: absolute; bottom: 0; left: 0; right: 0; }
.wave-wrap svg { width: 100%; height: 60px; display: block; }

/* ===== SERVICES ===== */
.section-services { padding: 100px 0; background: #fff; }
.cards { display: grid; grid-template-columns: repeat(3,1fr); gap: 28px; }
.card {
  background: var(--o-bg); border: 1px solid var(--o-border);
  border-radius: var(--rad); padding: 36px 28px; transition: all .3s ease;
}
.card:hover { transform: translateY(-8px); box-shadow: var(--shadow-lg); background: #fff; }
.card-ico {
  width: 68px; height: 68px; background: #fff;
  border-radius: 18px; display: flex; align-items: center; justify-content: center;
  margin-bottom: 20px; box-shadow: 0 4px 16px rgba(240,90,40,.12);
  color: var(--o);
}
.card h3 { font-size: 1.2rem; font-weight: 700; color: var(--black); margin-bottom: 10px; }
.card p  { color: var(--muted); font-size: .93rem; line-height: 1.72; }

/* ===== SHOWCASE ===== */
.section-showcase { padding: 0 0 80px; background: #fff; }
.section-showcase img { border-radius: 20px; box-shadow: var(--shadow-lg); }

/* ===== STORY ===== */
.section-story { padding: 100px 0; background: var(--o-bg); }
.story-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 80px; align-items: center; }
.story-text h2 { font-size: clamp(2rem, 4vw, 2.8rem); font-weight: 800; color: var(--black); margin-bottom: 32px; }
.story-text h2 span { color: var(--o); }
.story-pt { display: flex; gap: 18px; margin-bottom: 24px; }
.pt-ico {
  flex-shrink: 0; width: 44px; height: 44px; border-radius: 12px;
  background: rgba(240,90,40,.1); color: var(--o);
  display: flex; align-items: center; justify-content: center;
}
.story-pt h4 { font-size: .82rem; font-weight: 700; text-transform: uppercase; letter-spacing: .08em; color: var(--o); margin-bottom: 6px; }
.story-pt p  { color: var(--text); font-size: .92rem; line-height: 1.72; }
.story-text blockquote {
  margin-top: 32px; padding: 20px 24px;
  background: rgba(240,90,40,.08); border-left: 4px solid var(--o);
  border-radius: 0 12px 12px 0; font-style: italic; color: var(--text);
  font-size: .95rem; line-height: 1.75;
}
.story-img img { width: 100%; border-radius: 20px; box-shadow: var(--shadow); }

/* ===== COVERAGE ===== */
.section-coverage {
  padding: 100px 0;
  background: linear-gradient(135deg, #E04A18 0%, var(--o) 100%);
  color: #fff; text-align: center;
}
.cov-inner { display: flex; flex-direction: column; align-items: center; }
.cov-inner h2 {
  font-size: clamp(1.8rem, 4vw, 3rem); font-weight: 800;
  margin-bottom: 20px; line-height: 1.2;
}
.cov-inner h2 span {
  text-decoration: underline; text-decoration-color: rgba(255,255,255,.4);
  text-underline-offset: 6px;
}
.cov-inner > p {
  font-size: 1.05rem; opacity: .88; max-width: 540px;
  margin-bottom: 56px; line-height: 1.8;
}
.stats { display: flex; align-items: center; margin-bottom: 48px; }
.stat { text-align: center; padding: 0 48px; }
.stat b    { display: block; font-size: clamp(2.4rem, 5vw, 4rem); font-weight: 900; }
.stat span { font-size: .82rem; opacity: .75; text-transform: uppercase; letter-spacing: .1em; }
.stat-line { width: 1px; height: 56px; background: rgba(255,255,255,.25); }
.cov-tags { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; }
.cov-tags span {
  background: rgba(255,255,255,.12); border: 1px solid rgba(255,255,255,.25);
  padding: 6px 16px; border-radius: 50px; font-size: .82rem;
}

/* ===== NOTIFY ===== */
.section-notify { padding: 100px 0; background: var(--o-bg); }
.notify-box {
  background: #fff; border-radius: 24px; padding: 60px 48px;
  text-align: center; max-width: 600px; margin: 0 auto; box-shadow: var(--shadow-lg);
}
.notify-rocket { color: var(--o); margin-bottom: 16px; display: flex; justify-content: center; }
.notify-box h2 { font-size: 1.9rem; font-weight: 800; margin-bottom: 14px; color: var(--black); }
.notify-box > p { color: var(--muted); line-height: 1.75; margin-bottom: 32px; }
.form-row { display: flex; gap: 10px; }
.form-row input {
  flex: 1; padding: 13px 20px;
  border: 2px solid var(--o-border); border-radius: 50px;
  font-size: .95rem; font-family: inherit; outline: none;
  transition: border-color .25s; color: var(--text);
}
.form-row input:focus { border-color: var(--o); }
.form-row input:disabled { background: #f5f5f5; }
.notify-form { margin-bottom: 16px; }
.success-msg { color: #2e7d32; font-weight: 600; font-size: .95rem; margin-bottom: 10px; }
.fine-print { color: var(--muted); font-size: .82rem; }

/* ===== FOOTER ===== */
.footer { background: #111; color: #fff; padding: 64px 0 28px; }
.foot-row {
  display: grid; grid-template-columns: 1.5fr 1fr 1fr;
  gap: 48px; margin-bottom: 48px;
}
.foot-logo-img { width: 48px; height: 48px; border-radius: 12px; margin-bottom: 12px; }
.foot-logo { display: block; font-size: 1.8rem; font-weight: 800; margin-bottom: 10px; color: #fff; }
.foot-logo strong { color: var(--o); }
.foot-brand p     { color: rgba(255,255,255,.5); font-size: .9rem; margin-bottom: 4px; }
.foot-loc         { font-size: .8rem !important; color: rgba(255,255,255,.3) !important; }
.foot-col h5 {
  font-size: .78rem; font-weight: 600; text-transform: uppercase;
  letter-spacing: .1em; color: rgba(255,255,255,.35); margin-bottom: 16px;
}
.foot-col { display: flex; flex-direction: column; gap: 10px; }
.foot-col a    { color: rgba(255,255,255,.65); font-size: .92rem; transition: color .25s; }
.foot-col a:hover { color: var(--o); }
.foot-tag { color: rgba(255,255,255,.55); font-size: .88rem; }
.foot-bottom { border-top: 1px solid rgba(255,255,255,.08); padding-top: 24px; text-align: center; }
.foot-bottom p { color: rgba(255,255,255,.3); font-size: .82rem; }

/* ===== RESPONSIVE ===== */
@media (max-width: 1024px) {
  .hero-inner { flex-direction: column; text-align: center; padding-top: 100px; padding-bottom: 90px; }
  .hero-img   { flex: none; max-width: 480px; width: 100%; }
  .hero-text > p  { margin-left: auto; margin-right: auto; }
  .hero-chips { justify-content: center; }
  .hero-btns  { justify-content: center; }
  .cards      { grid-template-columns: 1fr; max-width: 440px; margin: 0 auto; }
  .story-wrap { grid-template-columns: 1fr; gap: 48px; }
  .story-img  { order: -1; max-width: 500px; margin: 0 auto; }
  .foot-row   { grid-template-columns: 1fr 1fr; }
}

@media (max-width: 768px) {
  .nav-links {
    display: none; position: fixed; inset: 0;
    background: #fff; flex-direction: column;
    justify-content: center; align-items: center;
    gap: 32px; z-index: 199;
  }
  .nav-links.is-open { display: flex; }
  .nav-links a { font-size: 1.3rem; color: var(--text) !important; }
  .navbar.is-scrolled .nav-links a { color: var(--text) !important; }
  .nav-btn {
    background: var(--o) !important; border-color: var(--o) !important;
    color: #fff !important; padding: 12px 28px !important;
    border-radius: 50px !important; border: 2px solid transparent !important;
  }
  .menu-toggle { display: flex; }
  .hero-img   { display: none; }
  .wave-wrap svg { height: 36px; }
  .stats      { flex-direction: column; gap: 28px; }
  .stat-line  { width: 60px; height: 1px; }
  .stat       { padding: 0; }
  .notify-box { padding: 40px 20px; }
  .form-row   { flex-direction: column; }
  .foot-row   { grid-template-columns: 1fr; gap: 32px; }
  .section-showcase { padding: 0 0 60px; }
}
</style>
