<!--Chloe Kruger u24569624-->
<script>
import { ref, onMounted } from 'vue'

export default {
  name: 'ProjectsPage',
  setup() {
    const breeds = ref([])

    const fetchBreeds = async () => {
      try {
        const response = await fetch('https://dog.ceo/api/breeds/list/random/3')
        const data = await response.json()
        if (response.ok && data.status === 'success') {
          breeds.value = data.message.map((breed, index) => ({
            id: index + 1,
            name: breed.charAt(0).toUpperCase() + breed.slice(1)
          }))
        } else {
          console.error('Error fetching dog breeds:', data.message)
        }
      } catch (error) {
        console.error('Error fetching dog breeds:', error)
      }
    }

    onMounted(fetchBreeds)

    return { breeds }
  }
}
</script>

<template>
  <div class="container mx-auto p-4">
    <section class="section-box">
      <h2>My Projects</h2>
      <p>A selection of web projects I’ve worked on:</p>
      <ul class="projects-list">
        <li>
          A e-commerce website for 216:
          <a href="https://wheatley.cs.up.ac.za/u24569624/index.html" target="_blank" class="link">Visit</a>
          <p><strong>Username:</strong> u24569624<br /><strong>Password:</strong> S_YAWja3ZQd*ppv</p>
        </li>
        <li>
          VIO comic book cover:<br>
          <img src="/public/images/VIO.png" alt="VIO Comic Cover" class="project-image" />
        </li>
        <li>
          211 Blender 3D lighting:<br>
          <img src="/public/images/211.png" alt="Blender Lighting" class="project-image" />
        </li>
      </ul>
    </section>

    <hr class="divider" />

    <section class="section-box">
      <h1>Dog Breeds</h1>
      <p>Discover some dog breeds, curated from the Dog API.</p>
      <ul v-if="breeds.length">
        <li v-for="breed in breeds" :key="breed.id">
          <strong>Breed {{ breed.id }}:</strong> {{ breed.name }}
        </li>
      </ul>
      <p v-else>Loading dog breeds...</p>
    </section>
  </div>
</template>

<style scoped>
.container {
  max-width: 1100px;
  background-color: rgba(255, 255, 255, 0.85);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
}

.dark .container {
  background-color: rgba(59, 59, 59, 0.9);
  color: #f3f4f6;
}

.section-box {
  background-color: rgba(255, 255, 255, 0.85);
  padding: 1.5rem;
  margin-bottom: 2rem;
  border-radius: 12px;
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.05);
}

.dark .section-box {
  background-color: rgba(47, 47, 47, 0.9);
}

h1, h2 {
  font-family: 'Playfair Display', serif;
  font-size: 1.75rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
}

ul {
  list-style: disc;
  padding-left: 1.5rem;
  margin-top: 1rem;
}

li {
  margin-bottom: 1.25rem;
  font-size: 1.1rem;
  line-height: 1.6;
}

img.project-image {
  width: 100%;
  max-width: 500px;
  height: auto;
  margin-top: 0.5rem;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.link {
  color: #0FA3B1;
  text-decoration: underline;
  margin-left: 5px;
}

.link:hover {
  color: #0c8794;
}

.divider {
  margin: 2rem 0;
  border: none;
  border-top: 1px solid rgba(128, 128, 128, 0.3);
}

@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }

  img.project-image {
    max-width: 100%;
  }
}
</style>
