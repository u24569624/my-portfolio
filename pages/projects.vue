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
    <h1>Dog Breeds</h1>
    <p>Discover some dog breeds, curated from the Dog API.</p>
    <ul v-if="breeds.length">
      <li v-for="breed in breeds" :key="breed.id">
        <strong>Breed {{ breed.id }}:</strong> {{ breed.name }}
      </li>
    </ul>
    <p v-else>Loading dog breeds...</p>
  </div>
</template>

<style scoped>
.container {
  background-color: rgba(255, 255, 255, 0.85);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
}

.dark .container {
  background-color: rgba(59, 59, 59, 0.9);
}

ul {
  list-style: disc;
  padding-left: 1.5rem;
  margin-top: 1rem;
}

li {
  margin-bottom: 1rem;
  font-size: 1.1rem;
}

@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }
}
</style>