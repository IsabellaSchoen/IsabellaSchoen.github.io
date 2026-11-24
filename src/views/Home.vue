<template>
  <main class="home">

    <!-- Hero -->
    <header class="hero">
      <div class="container-x hero-inner">
        <div class="hero-photo">
          <!-- Put the link/path to your picture into photoUrl in the script section below -->
          <img v-if="photoUrl" :src="photoUrl" alt="Isabella Schön">
          <div v-else class="photo-placeholder">
            <b-icon icon="person-fill"></b-icon>
          </div>
        </div>

        <div class="hero-text">
          <p class="eyebrow">Cognitive Science · Computer Science · Neuroscience</p>
          <h1>Isabella Schön</h1>
          <p class="lead-text">
            Cognitive scientist with a background in applied computer science, combining
            artificial intelligence and neuroscience to advance clinical brain research.
          </p>
          <p class="location">
            <b-icon icon="geo-alt"></b-icon> Tübingen, Germany
          </p>

          <div class="hero-buttons">
            <a class="btn-primary-x" :href="linkedin" target="_blank" rel="noopener">
              <b-icon icon="linkedin"></b-icon> Connect on LinkedIn
            </a>
            <a class="btn-outline-x" :href="github" target="_blank" rel="noopener">
              <b-icon icon="github"></b-icon> GitHub
            </a>
          </div>
        </div>
      </div>
    </header>

    <!-- About -->
    <section id="about" class="section">
      <div class="container-x">
        <h2 class="section-title">About me</h2>
        <div class="about-grid">
          <div class="about-text">
            <p>
              I hold a Bachelor's degree in Applied Computer Science from HTWG Konstanz and a
              Master's degree in Cognitive Science from the University of Tübingen, including a
              semester abroad at the Università di Trento.
            </p>
            <p>
              For my Master's thesis at the Hertie Institute for Clinical Brain Research, I studied
              <em>Scn1a</em> variants in migraine and epilepsy mouse models using multielectrode array
              recordings, and analysed the network activity in Python. Before that, I built
              knowledge graphs and AI ontologies at Robert Bosch GmbH and applied neural-network-based
              active learning in an industrial setting.
            </p>
            <p>
              I am interested in bringing data science and AI methods into neuroscience research,
              particularly where they help us understand neurological disorders.
            </p>
          </div>
          <ul class="facts">
            <li v-for="fact in facts" :key="fact.label">
              <span class="fact-label">{{ fact.label }}</span>
              <template v-if="Array.isArray(fact.value)">
                <span v-for="v in fact.value" :key="v" class="fact-value">{{ v }}</span>
              </template>
              <span v-else class="fact-value">{{ fact.value }}</span>
            </li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Experience -->
    <section id="experience" class="section section-alt">
      <div class="container-x">
        <h2 class="section-title">Research &amp; work experience</h2>
        <div class="timeline">
          <article v-for="item in experience" :key="item.title + item.org" class="timeline-item">
            <div class="timeline-meta">
              <span class="dates">{{ item.dates }}</span>
              <span class="place">{{ item.place }}</span>
            </div>
            <div class="timeline-body">
              <h3>{{ item.title }}</h3>
              <p class="org">{{ item.org }}</p>
              <ul>
                <li v-for="point in item.points" :key="point">{{ point }}</li>
              </ul>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Education -->
    <section id="education" class="section">
      <div class="container-x">
        <h2 class="section-title">Education</h2>
        <div class="timeline">
          <article v-for="item in education" :key="item.title + item.org" class="timeline-item">
            <div class="timeline-meta">
              <span class="dates">{{ item.dates }}</span>
              <span class="place">{{ item.place }}</span>
            </div>
            <div class="timeline-body">
              <h3>{{ item.title }}</h3>
              <p class="org">{{ item.org }}</p>
              <p v-if="item.thesis" class="detail">
                <span class="detail-label">Thesis:</span> {{ item.thesis }}
              </p>
              <p v-if="item.courses" class="detail">
                <span class="detail-label">Courses:</span> {{ item.courses }}
              </p>
            </div>
          </article>
        </div>
      </div>
    </section>

    <!-- Skills -->
    <section id="skills" class="section section-alt">
      <div class="container-x">
        <h2 class="section-title">Skills</h2>
        <div class="skills-grid">
          <div v-for="group in skills" :key="group.label" class="panel">
            <h3>{{ group.label }}</h3>
            <ul class="tags">
              <li v-for="tag in group.items" :key="tag">{{ tag }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects -->
    <section id="projects" class="section">
      <div class="container-x">
        <h2 class="section-title">Projects</h2>
        <div class="projects-grid">
          <div v-for="project in projects" :key="project.name" class="panel project-card">
            <p class="project-kind">{{ project.kind }}</p>
            <h3>{{ project.name }}</h3>
            <p>{{ project.description }}</p>
            <ul class="tags">
              <li v-for="tag in project.tags" :key="tag">{{ tag }}</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact" class="section contact">
      <div class="container-x contact-inner">
        <h2>Let's connect</h2>
        <p>
          I'm open to opportunities in neuroscience research, data science and AI.
          Feel free to reach out on LinkedIn.
        </p>
        <div class="hero-buttons contact-buttons">
          <a class="btn-light-x" :href="linkedin" target="_blank" rel="noopener">
            <b-icon icon="linkedin"></b-icon> LinkedIn
          </a>
          <a class="btn-ghost-x" :href="github" target="_blank" rel="noopener">
            <b-icon icon="github"></b-icon> GitHub
          </a>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      // Paste the link to your picture here, e.g. 'https://example.com/me.jpg',
      // or place a file in /public (e.g. public/me.jpg) and use 'me.jpg'.
      photoUrl: 'isabella-schoen.jpg',
      linkedin: 'https://www.linkedin.com/in/isabella-sch%C3%B6n-854311211/',
      github: 'https://github.com/IsabellaSchoen',

      facts: [
        { label: 'Degrees', value: ['M.Sc. Cognitive Science', 'B.Sc. Applied Computer Science'] },
        { label: 'Interests', value: 'AI, neurological diseases, brain research' },
        { label: 'Languages', value: 'German, English, Italian' }
      ],

      experience: [
        {
          dates: '08/2025 – 12/2025',
          place: 'Tübingen, Germany',
          title: 'Lab Internship',
          org: 'Hertie Institute for Clinical Brain Research',
          points: [
            'Recorded network activity in the Scn1a loss-of-function epilepsy mouse model using microelectrode arrays',
            'Analysed recordings in Python, including seizure-like event detection and network analysis'
          ]
        },
        {
          dates: '01/2023 – 10/2023',
          place: 'Stuttgart, Germany',
          title: 'PreMaster Program',
          org: 'Robert Bosch GmbH',
          points: [
            'Developed AI ontologies and contributed to knowledge management',
            'Modelled domain knowledge, built a knowledge graph and supported AI use cases'
          ]
        },
        {
          dates: '03/2020 – 08/2020',
          place: 'Munich, Germany',
          title: 'Internship, Software Development & Testing',
          org: 'Konzept IS',
          points: [
            'Designed and executed manual software tests',
            'Worked with C++, C#, Qt Creator, Visual Studio and Linux'
          ]
        }
      ],

      education: [
        {
          dates: '10/2023 – 10/2026',
          place: 'Tübingen, Germany',
          title: 'Master of Science, Cognitive Science',
          org: 'University of Tübingen',
          thesis: '“Functional and comparative analysis of Scn1a variants in migraine and epilepsy mouse models using multielectrode array” (Hertie Institute for Clinical Brain Research)'
        },
        {
          dates: '02/2025 – 08/2025',
          place: 'Trento, Italy',
          title: 'Semester Abroad, Scienze Cognitive',
          org: 'Università di Trento',
          courses: 'Visual Brain and Design, Affective Neuroscience, Limbic System (anatomy, physiopathology, immunology)'
        },
        {
          dates: '09/2018 – 08/2022',
          place: 'Konstanz, Germany',
          title: 'Bachelor of Science, Applied Computer Science',
          org: 'HTWG Konstanz',
          thesis: '“Application of Active Learning based on Neural Networks in an industrial environment” (Baumer Inspection)'
        }
      ],

      skills: [
        { label: 'Programming', items: ['Python', 'C'] },
        { label: 'Data Science', items: ['pandas', 'NumPy', 'matplotlib', 'seaborn'] },
        { label: 'Neuroscience Methods', items: ['Multielectrode array (MEA) recordings', 'Electrophysiological data analysis'] },
        { label: 'Tools', items: ['Git', 'Linux', 'Jupyter Notebook', 'VS Code'] },
        { label: 'Languages', items: ['German (native)', 'English (advanced)', 'Italian (basic)'] }
      ],

      projects: [
        {
          kind: 'Personal project',
          name: 'MyGraine',
          description: 'A personal migraine diary that tracks daily food and fluid intake, timestamps and symptom patterns, to identify potential associations between dietary habits and migraine symptoms.',
          tags: ['Health data', 'Pattern analysis', 'Claude Code']
        }
      ]
    }
  }
};
</script>

<style>
.container-x {
  max-width: var(--maxw);
  margin: 0 auto;
  padding: 0 24px;
}

/* Hero */
.hero {
  padding: 96px 0 88px;
  border-bottom: 1px solid var(--line);
}

.hero-inner {
  display: flex;
  align-items: center;
  gap: 56px;
}

.hero-photo {
  flex-shrink: 0;
}

.hero-photo img,
.photo-placeholder {
  display: block;
  width: 220px;
  height: 220px;
  border-radius: 50%;
  object-fit: cover;
  box-shadow: 0 0 0 6px var(--surface), 0 0 0 7px var(--line);
}

.photo-placeholder {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #e9e4d8;
  color: #8a8478;
  font-size: 104px;
}

.eyebrow {
  text-transform: uppercase;
  letter-spacing: 0.14em;
  font-size: 0.78rem;
  font-weight: 600;
  color: var(--accent);
  margin: 0 0 12px;
}

.hero h1 {
  font-size: clamp(2.2rem, 5vw, 3.2rem);
  font-weight: 700;
  color: var(--navy);
  margin: 0 0 16px;
  line-height: 1.1;
}

.lead-text {
  font-size: 1.15rem;
  line-height: 1.65;
  color: var(--text);
  max-width: 58ch;
  margin: 0 0 12px;
}

.location {
  color: var(--muted);
  font-size: 0.95rem;
  margin: 0;
}

.hero-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 28px;
}

.btn-primary-x,
.btn-outline-x,
.btn-light-x,
.btn-ghost-x {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  border-radius: 999px;
  font-size: 0.95rem;
  font-weight: 500;
  text-decoration: none !important;
  transition: background 0.15s, color 0.15s, border-color 0.15s;
}

.btn-primary-x {
  background: var(--navy);
  color: #fff !important;
  border: 1px solid var(--navy);
}

.btn-primary-x:hover {
  background: var(--navy-soft);
}

.btn-outline-x {
  color: var(--navy) !important;
  border: 1px solid #c9c6bd;
  background: transparent;
}

.btn-outline-x:hover {
  border-color: var(--navy);
  background: var(--surface);
}

/* Sections */
.section {
  padding: 80px 0;
}

.section-alt {
  background: var(--surface);
  border-top: 1px solid var(--line);
  border-bottom: 1px solid var(--line);
}

.section-title {
  font-size: 0.85rem;
  text-transform: uppercase;
  letter-spacing: 0.16em;
  font-weight: 700;
  color: var(--navy);
  margin: 0 0 40px;
  padding-bottom: 12px;
  border-bottom: 2px solid var(--navy);
  display: inline-block;
}

.section p {
  line-height: 1.7;
}

/* About */
.about-grid {
  display: grid;
  grid-template-columns: 1.7fr 1fr;
  gap: 56px;
  align-items: start;
}

.about-text p {
  font-size: 1.05rem;
  margin: 0 0 16px;
}

.facts {
  list-style: none;
  margin: 0;
  padding: 24px;
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius);
}

.facts li {
  display: flex;
  flex-direction: column;
  padding: 12px 0;
  border-bottom: 1px solid var(--line);
}

.facts li:first-child { padding-top: 0; }
.facts li:last-child { border-bottom: 0; padding-bottom: 0; }

.fact-label {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--muted);
}

.fact-value {
  font-weight: 600;
  color: var(--navy);
}

/* Timeline */
.timeline-item {
  display: grid;
  grid-template-columns: 190px 1fr;
  gap: 32px;
  padding: 28px 0;
  border-bottom: 1px solid var(--line);
}

.timeline-item:first-child { padding-top: 0; }
.timeline-item:last-child { border-bottom: 0; padding-bottom: 0; }

.timeline-meta {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.dates {
  font-weight: 600;
  color: var(--navy);
  font-size: 0.95rem;
}

.place {
  color: var(--muted);
  font-size: 0.9rem;
  font-style: italic;
}

.timeline-body h3 {
  font-size: 1.15rem;
  font-weight: 700;
  color: var(--navy);
  margin: 0 0 2px;
}

.org {
  color: var(--accent);
  font-weight: 500;
  margin: 0 0 10px;
}

.timeline-body ul {
  margin: 0;
  padding-left: 18px;
}

.timeline-body li {
  line-height: 1.65;
  margin-bottom: 4px;
}

.detail {
  margin: 0 0 6px;
}

.detail-label {
  font-weight: 600;
  color: var(--navy);
}

/* Cards */
.panel {
  background: var(--surface);
  border: 1px solid var(--line);
  border-radius: var(--radius);
  padding: 24px;
}

.section-alt .panel {
  background: var(--bg);
}

.panel h3 {
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--navy);
  margin: 0 0 14px;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 20px;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.tags li {
  font-size: 0.85rem;
  padding: 5px 12px;
  border-radius: 999px;
  background: #eef1f7;
  color: var(--navy-soft);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 20px;
}

.project-card p {
  margin: 0 0 18px;
}

.project-kind {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--muted);
  margin: 0 0 6px !important;
}

/* Contact */
.contact {
  background: var(--navy);
  color: #fff;
  text-align: center;
}

.contact h2 {
  font-size: 2rem;
  font-weight: 700;
  color: #fff;
  margin: 0 0 12px;
}

.contact p {
  color: rgba(255, 255, 255, 0.8);
  font-size: 1.05rem;
  max-width: 52ch;
  margin: 0 auto;
}

.contact-buttons {
  justify-content: center;
}

.btn-light-x {
  background: #fff;
  color: var(--navy) !important;
  border: 1px solid #fff;
}

.btn-light-x:hover {
  background: #e8ebf2;
}

.btn-ghost-x {
  color: #fff !important;
  border: 1px solid rgba(255, 255, 255, 0.4);
}

.btn-ghost-x:hover {
  border-color: #fff;
  background: rgba(255, 255, 255, 0.08);
}

/* Responsive */
@media (max-width: 860px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 32px;
  }
}

@media (max-width: 700px) {
  .hero {
    padding: 56px 0;
  }
  .hero-inner {
    flex-direction: column;
    text-align: center;
    gap: 28px;
  }
  .hero-photo img,
  .photo-placeholder {
    width: 160px;
    height: 160px;
    font-size: 76px;
  }
  .lead-text {
    margin-left: auto;
    margin-right: auto;
  }
  .hero-buttons {
    justify-content: center;
  }
  .section {
    padding: 56px 0;
  }
  .timeline-item {
    grid-template-columns: 1fr;
    gap: 8px;
  }
  .timeline-meta {
    flex-direction: row;
    flex-wrap: wrap;
    gap: 4px 12px;
  }
  .projects-grid,
  .skills-grid {
    grid-template-columns: 1fr;
  }
}
</style>
