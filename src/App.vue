/* the output */
<template>
  <div class="main-content">
    <header class="intro">
      <div class="intro-photo">
        <!-- TODO: put the link to your picture into photoUrl below (in the script section) -->
        <img v-if="photoUrl" :src="photoUrl" alt="Isabella Schön" />
        <div v-else class="photo-placeholder">
          <b-icon icon="person-fill"></b-icon>
        </div>
      </div>

      <div class="intro-text">
        <h1>Isabella Schön</h1>
        <p>
          I hold a Bachelor's degree in Applied Computer Science and a Master's
          degree in Cognitive Science. I am interested in combining artificial
          intelligence and cognitive science to drive progress in clinical brain
          research.
        </p>

        <div class="intro-buttons">
          <b-button
            variant="outline-dark"
            href="https://www.linkedin.com/in/isabella-schoen/"
            target="_blank"
            rel="noopener"
          >
            <b-icon icon="linkedin"></b-icon>
            LinkedIn
          </b-button>
          <b-button
            variant="outline-dark"
            href="https://github.com/IsabellaSchoen"
            target="_blank"
            rel="noopener"
          >
            <b-icon icon="github"></b-icon>
            GitHub
          </b-button>
        </div>
      </div>
    </header>
    <router-view />
  </div>
</template>

/* the logic: the javascript */
<script>
export default {
  name: "App",
  data() {
    return {
      // Paste the link to your picture here, e.g. 'https://example.com/me.jpg'
      photoUrl: "",
    };
  },
};
</script>

/* the styling */
<style>
html,
body {
  margin: 0;
  background-color: floralwhite !important;
}

.main-content {
  font-family: Avenir, "Helvetica Neue", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 48px 16px;
  box-sizing: border-box;
}

.intro {
  display: flex;
  align-items: center;
  gap: 48px;
  max-width: 880px;
  margin: 0 auto;
  text-align: left;
}

.intro-photo {
  flex-shrink: 0;
}

.intro-photo img,
.photo-placeholder {
  display: block;
  width: 200px;
  height: 200px;
  border-radius: 50%;
  object-fit: cover;
}

.photo-placeholder {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #e9e4d8;
  color: #8a8478;
  font-size: 96px;
}

.intro-text h1 {
  color: black;
  font-size: clamp(2rem, 5vw, 2.75rem);
  font-weight: 600;
  margin: 0 0 16px;
}

.intro-text p {
  color: black;
  font-size: 1.125rem;
  line-height: 1.6;
  max-width: 60ch;
  margin: 0;
}

.intro-buttons {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 24px;
}

.intro-buttons .btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

@media (max-width: 700px) {
  .intro {
    flex-direction: column;
    gap: 24px;
    text-align: center;
  }
  .intro-photo img,
  .photo-placeholder {
    width: 150px;
    height: 150px;
    font-size: 72px;
  }
  .intro-text p {
    margin: 0 auto;
  }
  .intro-buttons {
    justify-content: center;
  }
}
</style>
