<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script setup lang="ts">
// App utama yang akan menampilkan semua komponen
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  line-height: 1.6;
  color: #f8fafc;
  background: #0f172a;
}

#app {
  min-height: 100vh;
  background: #0f172a;
}
</style>