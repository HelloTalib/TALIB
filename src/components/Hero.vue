<template>
  <section class="hero">
    <!-- Animated gradient mesh background -->
    <div class="hero-mesh" aria-hidden="true">
      <div class="blob-wrap" :style="blobStyle(0)">
        <div class="mesh-blob mesh-blob-1"></div>
      </div>
      <div class="blob-wrap" :style="blobStyle(1)">
        <div class="mesh-blob mesh-blob-2"></div>
      </div>
      <div class="blob-wrap" :style="blobStyle(2)">
        <div class="mesh-blob mesh-blob-3"></div>
      </div>
    </div>

    <!-- Dark vignette overlay -->
    <div class="hero-vignette" aria-hidden="true"></div>

    <!-- Content -->
    <div class="hero-content">
      <div class="hero-inner">
        <div class="hero-eyebrow hero-anim" style="animation-delay:0s">
          <span class="eyebrow-line" aria-hidden="true"></span>
          <span>Hello, I am</span>
        </div>

        <h1 class="hero-name">
          <span class="name-line name-reveal" style="animation-delay:0.08s">ABU</span>
          <span class="name-line gradient-text name-reveal" style="animation-delay:0.26s">TALIB</span>
        </h1>

        <div class="hero-role hero-anim" style="animation-delay:0.55s">
          Software Developer&nbsp;&nbsp;·&nbsp;&nbsp;WordPress Developer
        </div>

        <div class="hero-cta hero-anim" style="animation-delay:0.72s">
          <a href="#portfolio" class="btn-primary">
            <span>View My Work</span>
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
              <path d="M7 17L17 7M17 7H7M17 7v10"/>
            </svg>
          </a>
          <a
            href="https://drive.google.com/file/d/1fv4O3MIylENtRadVWQRKjVlqe0V1uF5z/view?usp=sharing"
            target="_blank"
            rel="noopener noreferrer"
            class="btn-ghost"
          >Download CV</a>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <a href="#about" class="scroll-cue" aria-label="Scroll to About section">
      <span class="scroll-label">scroll</span>
      <span class="scroll-track" aria-hidden="true">
        <span class="scroll-dot"></span>
      </span>
    </a>
  </section>
</template>

<script>
import heroImage from "@/assets/hero.jpg";

export default {
  data() {
    return {
      heroImage,
      mx: 0, my: 0,
      cx: 0, cy: 0,
      rafId: null,
      reduced: false,
    };
  },
  mounted() {
    this.reduced = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
    if (!this.reduced) {
      window.addEventListener("mousemove", this.onMouseMove, { passive: true });
      this.animateParallax();
    }
  },
  beforeUnmount() {
    window.removeEventListener("mousemove", this.onMouseMove);
    cancelAnimationFrame(this.rafId);
  },
  methods: {
    onMouseMove(e) {
      this.mx = (e.clientX / window.innerWidth)  - 0.5;
      this.my = (e.clientY / window.innerHeight) - 0.5;
    },
    animateParallax() {
      this.cx += (this.mx - this.cx) * 0.055;
      this.cy += (this.my - this.cy) * 0.055;
      this.rafId = requestAnimationFrame(this.animateParallax);
    },
    blobStyle(idx) {
      const speeds = [[55, 38], [-38, 52], [28, -44]];
      const [sx, sy] = speeds[idx];
      return { transform: `translate(${this.cx * sx}px, ${this.cy * sy}px)` };
    },
  }
};
</script>

<style scoped>
/* ── Shell ── */
.hero {
  position: relative;
  height: 100vh;
  min-height: 640px;
  overflow: hidden;
  display: flex;
  align-items: center;
  padding-top: var(--nav-height);
}

/* ── Gradient Mesh ── */
.hero-mesh {
  position: absolute;
  inset: 0;
  overflow: hidden;
}
.blob-wrap {
  position: absolute;
  inset: 0;
  will-change: transform;
  transition: transform 0.05s linear;
}
.mesh-blob {
  position: absolute;
  border-radius: 50%;
  filter: blur(90px);
  opacity: 0.35;
  will-change: transform;
}
.mesh-blob-1 {
  width: 700px;
  height: 700px;
  background: radial-gradient(circle, rgba(110, 231, 183, 0.55) 0%, transparent 65%);
  top: -200px;
  left: -150px;
  animation: meshMove1 22s ease-in-out infinite;
}
.mesh-blob-2 {
  width: 550px;
  height: 550px;
  background: radial-gradient(circle, rgba(99, 102, 241, 0.45) 0%, transparent 65%);
  top: 30%;
  right: -100px;
  animation: meshMove2 28s ease-in-out infinite;
}
.mesh-blob-3 {
  width: 480px;
  height: 480px;
  background: radial-gradient(circle, rgba(14, 165, 233, 0.3) 0%, transparent 65%);
  bottom: -80px;
  left: 38%;
  animation: meshMove3 19s ease-in-out infinite;
}

@keyframes meshMove1 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33%       { transform: translate(60px, -40px) scale(1.1); }
  66%       { transform: translate(-30px, 50px) scale(0.93); }
}
@keyframes meshMove2 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33%       { transform: translate(-50px, 30px) scale(1.08); }
  66%       { transform: translate(40px, -60px) scale(1.12); }
}
@keyframes meshMove3 {
  0%, 100% { transform: translate(0, 0) scale(1); }
  50%       { transform: translate(-40px, -30px) scale(1.06); }
}

/* ── Vignette ── */
.hero-vignette {
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse 80% 70% at 50% 50%, transparent 20%, rgba(10, 10, 15, 0.6) 100%),
    linear-gradient(to bottom, rgba(10,10,15,0.3) 0%, transparent 40%, transparent 60%, rgba(10,10,15,0.9) 100%);
  pointer-events: none;
}

/* ── Entry animations ── */
@keyframes heroPop {
  from { opacity: 0; transform: translateY(18px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-anim {
  opacity: 0;
  animation: heroPop 0.65s cubic-bezier(0.2,0,0.1,1) both;
}
@keyframes nameReveal {
  from { clip-path: inset(0 102% 0 0); }
  to   { clip-path: inset(0 0%   0 0); }
}
.name-reveal {
  display: block;
  clip-path: inset(0 102% 0 0);
  animation: nameReveal 0.9s cubic-bezier(0.16,1,0.3,1) both;
}

/* ── Content ── */
.hero-content {
  position: relative;
  z-index: 1;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 48px;
}

.hero-eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 14px;
  font-family: var(--font-mono);
  font-size: 13px;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: var(--color-accent);
  margin-bottom: 20px;
}
.eyebrow-line {
  display: inline-block;
  width: 40px;
  height: 1px;
  background: var(--color-accent);
}

.hero-name {
  font-family: var(--font-display);
  font-weight: 800;
  font-size: clamp(72px, 13vw, 160px);
  line-height: 0.9;
  letter-spacing: -0.04em;
  display: flex;
  flex-direction: column;
  margin-bottom: 28px;
}
.name-line { display: block; }

.hero-role {
  font-size: 16px;
  font-weight: 400;
  color: var(--color-muted);
  letter-spacing: 0.05em;
  margin-bottom: 48px;
}

/* ── CTA Buttons ── */
.hero-cta {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  align-items: center;
}

.btn-primary {
  position: relative;
  overflow: hidden;
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  background: var(--color-accent);
  color: #0A0A0F;
  font-weight: 600;
  font-size: 14px;
  letter-spacing: 0.02em;
  border-radius: var(--radius-md);
  text-decoration: none;
  transition: filter var(--transition-base), transform var(--transition-base);
  will-change: transform;
}
.btn-primary::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 55%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.28), transparent);
  transform: skewX(-20deg);
  transition: left 0.55s ease;
}
.btn-primary:hover { filter: brightness(1.06); transform: translateY(-2px); }
.btn-primary:hover::after { left: 140%; }

.btn-ghost {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 14px 28px;
  border: 1px solid var(--color-border);
  border-radius: var(--radius-md);
  color: var(--color-text);
  font-weight: 500;
  font-size: 14px;
  letter-spacing: 0.02em;
  text-decoration: none;
  transition: border-color var(--transition-base), color var(--transition-base), transform var(--transition-base);
  will-change: transform;
}
.btn-ghost:hover {
  border-color: var(--color-accent-border);
  color: var(--color-accent);
  transform: translateY(-2px);
}

/* ── Scroll Cue ── */
.scroll-cue {
  position: absolute;
  bottom: 32px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  color: var(--color-muted);
  transition: color var(--transition-base);
}
.scroll-cue:hover { color: var(--color-accent); }
.scroll-label {
  font-family: var(--font-mono);
  font-size: 10px;
  letter-spacing: 0.3em;
  text-transform: uppercase;
}
.scroll-track {
  width: 1px;
  height: 48px;
  background: var(--color-border);
  display: block;
  position: relative;
  overflow: hidden;
}
.scroll-dot {
  position: absolute;
  top: -8px;
  left: 50%;
  transform: translateX(-50%);
  width: 3px;
  height: 8px;
  border-radius: 2px;
  background: var(--color-accent);
  animation: scrollDrop 1.8s ease-in-out infinite;
}
@keyframes scrollDrop {
  0%   { top: -8px; opacity: 1; }
  80%  { top: 48px; opacity: 0.2; }
  100% { top: 48px; opacity: 0; }
}

/* ── Responsive ── */
@media (max-width: 1024px) {
  .hero-content { padding: 0 32px; }
}
@media (max-width: 768px) {
  .hero-content { padding: 0 24px; }
  .hero-name { font-size: clamp(56px, 14vw, 100px); }
}
@media (max-width: 640px) {
  .hero-content { padding: 0 16px; }
  .hero-name { font-size: clamp(48px, 16vw, 80px); }
  .hero-role { font-size: 14px; }
}
</style>
