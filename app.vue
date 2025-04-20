<!-- Main Vue Component -->
<script setup>
import { ref } from 'vue'

const darkMode = ref(false)

function toggleDark() {
  darkMode.value = !darkMode.value
}
</script>

<template>
  <div :class="darkMode ? 'dark' : ''">
    <div class="top-nav">
      <h1 id="title">
        <span class="typewriter">Chloe Kruger</span>
      </h1>

      <nav>
        <ul>
          <li><NuxtLink to="/">Home</NuxtLink></li>
          <li><NuxtLink to="/projects">Projects</NuxtLink></li>
          <li><NuxtLink to="/contact">Contact</NuxtLink></li>
        </ul>
      </nav>

      <button class="toggle-mode" @click="toggleDark">
        {{ darkMode ? '🌞' : '🌙' }}
      </button>
    </div>

    <div id="content">
      <NuxtPage />
    </div>
  </div>
</template>

<!-- Google Fonts -->
<style>
@import url('https://fonts.googleapis.com/css2?family=Fira+Code&family=Roboto:wght@400;500&family=Playfair+Display:wght@600&display=swap');

#content{
  height: 100vh;
  padding: 1%;
}

h1{
 margin: 5px !important;
}

h1, h2, h3 {
  font-family: 'Playfair Display', serif;
  font-weight: 600;
}

body {
  font-family: 'Roboto', sans-serif;
  margin: 0;
  padding: 0;
  background-color: #F3F4F6;
  transition: background-color 0.3s ease, color 0.3s ease;
  color: #3B3B3B;
}

body .dark {
  background-color:#3B3B3B;
  color: #F3F4F6;
}
</style>

<!-- Component Styling -->
<style scoped>
.top-nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  padding: 1rem 2rem;
  background: rgba(28, 28, 28, 0.85);  /* Darker but with transparency */
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);  /* Soft border */
  border-radius: 0 0 12px 12px;
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.1);  /* Slight shadow for separation */
  position: sticky;
  top: 0;
  z-index: 999;
}

#title {
  font-family: 'Fira Code', monospace;
  font-size: 1.8rem;
  font-weight: 600;
  color: #F3F4F6;
  white-space: nowrap;
}


/* Typewriter animation */
.typewriter {
  display: inline-block;
  overflow: hidden;
  white-space: nowrap;
  border-right: 2px solid #F3F4F6;
  width: 0;
  animation: typing 4s steps(13, end) forwards, blink 0.6s step-end infinite;
}

@keyframes typing {
  from { width: 0 }
  to { width: 13ch }
}

@keyframes blink {
  50% { border-color: transparent }
}

nav ul {
  display: flex;
  list-style: none;
  gap: 1.5rem;
  margin: 0;
  padding: 0;
}

nav a {
  color: #F3F4F6;
  font-weight: 500;
  text-decoration: none;
  transition: color 0.3s ease;
}

nav a:hover {
  color: #0FA3B1;  /* Accent color for hover */
}

/* Toggle Button */
.toggle-mode {
  background: none;
  border: none;
  font-size: 1.5rem;
  color: #F3F4F6;
  cursor: pointer;
}

/* Dark Mode Overrides */
.dark .top-nav {
  background: rgba(0, 160, 160, 0.75);  /* Keep the glass effect */
  border-bottom: 1px solid rgba(47, 47, 47, 0.491);
  box-shadow: 0 6px 20px rgba(78, 78, 78, 0.574);  /* Slight shadow for separation */
}

.dark nav a:hover {
  color: #76428f  ;  /* Slightly muted color for hover in dark mode */
}
</style>
