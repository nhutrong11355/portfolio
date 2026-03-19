<template>
  <footer class="footer">
    <div class="container">
      <p>© {{ year }} Nguyen Nhu Trong. Built with Vue.js</p>
    </div>
  </footer>
</template>

<script setup>
const year = new Date().getFullYear()
</script>

<style scoped>
.footer {
  padding: 2rem;
  border-top: 1px solid rgba(255, 255, 255, 0.05);
  text-align: center;
}
.footer p {
  color: #475569;
  font-size: 0.85rem;
  margin: 0;
}
</style>
