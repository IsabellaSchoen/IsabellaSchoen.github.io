<template>
  <div class="site">
    <nav class="site-nav">
      <div class="nav-inner">
        <a class="nav-brand" href="#" @click.prevent="scrollTo('top')">Isabella Schön</a>
        <ul class="nav-links">
          <li v-for="link in navLinks" :key="link.id">
            <a href="#" @click.prevent="scrollTo(link.id)">{{ link.label }}</a>
          </li>
        </ul>
      </div>
    </nav>

    <router-view/>

    <footer class="footer">
      <div class="footer-inner">
        <span>© {{ year }} Isabella Schön</span>
        <span class="footer-links">
          <a :href="linkedin" target="_blank" rel="noopener">LinkedIn</a>
          <a :href="github" target="_blank" rel="noopener">GitHub</a>
        </span>
      </div>
    </footer>
  </div>
</template>


<script>
export default {
  name: 'App',
  data() {
    return {
      year: new Date().getFullYear(),
      linkedin: 'https://www.linkedin.com/in/isabella-sch%C3%B6n-854311211/',
      github: 'https://github.com/IsabellaSchoen',
      navLinks: [
        { id: 'about', label: 'About' },
        { id: 'experience', label: 'Experience' },
        { id: 'education', label: 'Education' },
        { id: 'skills', label: 'Skills' },
        { id: 'projects', label: 'Projects' },
        { id: 'contact', label: 'Contact' }
      ]
    }
  },
  methods: {
    // Hash routing owns the URL fragment, so in-page links scroll via JS.
    scrollTo(id) {
      if (id === 'top') {
        window.scrollTo({ top: 0, behavior: 'smooth' })
        return
      }
      const el = document.getElementById(id)
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
  }
}
</script>


<style>
:root {
  --navy: #1c2236;
  --navy-soft: #2d3552;
  --accent: #4a6fa5;
  --bg: #faf8f3;
  --surface: #ffffff;
  --text: #1f2430;
  --muted: #6b7080;
  --line: #e4e1d8;
  --radius: 12px;
  --maxw: 1040px;
}

html {
  scroll-padding-top: 80px;
}

body {
  margin: 0;
  background-color: var(--bg) !important;
  color: var(--text) !important;
  font-family: "Inter", "Helvetica Neue", Arial, sans-serif !important;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

a {
  color: var(--accent);
}

/* Navigation */
.site-nav {
  position: sticky;
  top: 0;
  z-index: 10;
  background: var(--navy);
}

.nav-inner {
  max-width: var(--maxw);
  margin: 0 auto;
  padding: 0 24px;
  height: 64px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
}

.nav-brand {
  color: #fff !important;
  font-weight: 600;
  font-size: 1.05rem;
  letter-spacing: 0.02em;
  text-decoration: none !important;
  white-space: nowrap;
}

.nav-links {
  display: flex;
  gap: 28px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links a {
  color: rgba(255, 255, 255, 0.75);
  font-size: 0.92rem;
  text-decoration: none;
  transition: color 0.15s;
}

.nav-links a:hover {
  color: #fff;
}

/* Footer */
.footer {
  background: var(--navy);
  color: rgba(255, 255, 255, 0.7);
  font-size: 0.9rem;
}

.footer-inner {
  max-width: var(--maxw);
  margin: 0 auto;
  padding: 24px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 12px;
}

.footer-links {
  display: flex;
  gap: 20px;
}

.footer-links a {
  color: rgba(255, 255, 255, 0.85);
  text-decoration: none;
}

.footer-links a:hover {
  color: #fff;
}

@media (max-width: 760px) {
  .nav-links {
    display: none;
  }
}
</style>
