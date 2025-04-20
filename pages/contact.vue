<!--Chloe Kruger u24569624-->
<script>
export default {
  name: 'ContactPage'
}
</script>

<template>
  <div class="container mx-auto p-4">
    <h1>Contact Me</h1>
    <form name="contact" method="POST" data-netlify="true" netlify-honeypot="bot-field">
      <input type="hidden" name="form-name" value="contact" />
      <p class="hidden">
        <label>Don’t fill this out: <input name="bot-field" /></label>
      </p>
      <input type="text" name="name" placeholder="Name" required />
      <input type="email" name="email" placeholder="Email" required />
      <textarea name="message" placeholder="Message" required></textarea>
      <button type="submit">Send</button>
    </form>
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

form {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  max-width: 600px;
  margin-top: 1rem;
}

.hidden {
  display: none;
}

input, textarea {
  padding: 0.75rem;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-size: 1rem;
  background-color: #fff;
  transition: border 0.3s ease;
}

textarea {
  resize: vertical;
  min-height: 150px;
}

input:focus, textarea:focus {
  border-color: #0FA3B1;
  outline: none;
}

button {
  padding: 0.75rem;
  background-color: #0FA3B1;
  color: white;
  border: none;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #0c8794;
}

@media (max-width: 768px) {
  .container {
    padding: 1rem;
  }
}
</style>