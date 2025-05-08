<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      Selamat datang di Aplikasi To-Do List Syafiq<br>
      <a href="https://www.instagram.com/" target="_blank" rel="noopener"><img src="../assets/instagram.svg" alt=""></a> 
      <a href="https://github.com/sapikkk/todo-list" target="_blank" rel="noopener"><img src="../assets/github.svg" alt=""></a>.
    </h3>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.0rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

img {
  width: 25px;
  margin-right: 10px;
}

img:hover{
  transform: scale(1.1);
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
