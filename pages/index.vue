<!--Chloe Kruger u24569624-->
<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'HomePage',
  setup() {
    const weather = ref(null)
    const city = 'Pretoria'
    const apiKey = '2253413a16643af214a5e7333b9982ef'

    const fetchWeather = async () => {
      try {
        const response = await fetch(
          `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`
        )
        const data = await response.json()
        if (response.ok) {
          weather.value = {
            temp: Math.round(data.main.temp),
            description: data.weather[0].description,
            icon: `http://openweathermap.org/img/wn/${data.weather[0].icon}.png`
          }
        } else {
          console.error('Error fetching weather:', data.message)
        }
      } catch (error) {
        console.error('Error:', error)
      }
    }

    onMounted(fetchWeather)

    return { weather }
  }
}
</script>

<template>
  <div class="container mx-auto p-4">
    <div class="image-container">
      <img src="/images/chloe.jpg" alt="Chloe Kruger" class="profile-image" />
    </div>

    <div class="bio">
      <h1>Welcome to My Portfolio</h1>
      <p>Hi, I’m Chloe Kruger — a BIS Multimedia student at the University of Pretoria.
        I'm passionate about web development, design, and learning how technology can solve real-world problems. I enjoy building clean, responsive websites and exploring new tools and frameworks.
        My goal is to grow as a developer by taking on meaningful projects, continuously learning, and collaborating with others.
        This portfolio showcases some of the work I’ve done so far — thanks for stopping by!</p>
      
      <div v-if="weather" class="weather">
        <h3>Current Weather in Pretoria</h3>
        <p>{{ weather.temp }}°C, {{ weather.description }}</p>
        <img :src="weather.icon" alt="Weather icon" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  background-color: rgba(255, 255, 255, 0.85);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  max-width: 1100px;
}

.dark .container {
  background-color: rgba(59, 59, 59, 0.9);
}

.image-container {
  text-align: center;
  margin-bottom: 1.5rem;
}

.profile-image {
  width: 200px;
  height: 200px;
  object-fit: cover;
  border-radius: 50%;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.bio {
  padding: 1rem;
  background-color: rgba(255, 255, 255, 0.85);
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
}

.dark .bio {
  background-color: rgba(59, 59, 59, 0.9);
}

.weather {
  margin-top: 1rem;
  padding: 1rem;
  background-color: rgba(0, 163, 177, 0.1);
  border-radius: 8px;
}

.weather img {
  width: 50px;
  vertical-align: middle;
}

@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }
  .profile-image {
    width: 150px;
    height: 150px;
  }
}
</style>